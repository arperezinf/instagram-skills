# Reglas de limpieza (Instagram, V3, 2026-09, adaptación al español)

Catálogos por niveles que aplica el humanizador. Carga este archivo cuando
realmente ejecutes una limpieza. Dos niveles: forense (siempre activo) y
estricto (activo por defecto), más las limpiezas de formato de Instagram. V3: el
vocabulario se puntúa por **densidad por párrafo**, no se borra palabra por
palabra. Las rayas se **limitan** a aproximadamente 1 cada 100 palabras, no se
prohíben. El ritmo forzado es un indicio, no una solución. Ver "Qué cambió en
V3" en SKILL.md para la evidencia.

**Nota sobre la adaptación:** los porcentajes y tasas de este archivo provienen
de estudios y de un corpus en inglés de la versión original. Los catálogos y
expresiones regulares en español son una adaptación por criterio lingüístico,
no una medición. Úsalos como guía y prioriza siempre el juicio sobre el texto
concreto. Los bloques de código son pseudocódigo de referencia que describe el
criterio; no hay que ejecutarlos.

## Contenido

- Puntuación por densidad (cómo se aplica cada regla de vocabulario)
- Nivel FORENSE (siempre activo)
- Nivel ESTRICTO (activo por defecto)
- Calcos del inglés (activo por defecto)
- Limpiezas de formato de Instagram (siempre se aplican)
- Pasada 2 - Ritmo (solo protección contra la uniformidad)
- Pasada 3 - Inserciones prohibidas (marcadores de sinceridad, atenuantes)
- Conservar esto (voz del usuario, no limpiar)

---

## Puntuación por densidad (cómo se aplica cada regla de vocabulario)

El principio de acumulación: los lectores detectan un texto de IA por
acumulación de marcadores, no por una palabra aislada. Un "fundamental" en un
párrafo es español normal. "Fundamental", "potenciar" y una cadena de
nominalizaciones en el mismo párrafo son una firma.

```python
def score_paragraph(paragraph: str, markers: dict) -> dict:
    """Cuenta coincidencias de marcadores por párrafo (o por slide de carrusel). Devuelve las coincidencias y la acción."""
    hits = []
    for name, pattern in markers.items():
        for m in re.finditer(pattern, paragraph, flags=re.I):
            hits.append((name, m.group(0)))
    n = len(hits)
    always = [h for h in hits if h[0] in ("reveal_bridge", "neg_parallel", "sincerity_marker")]
    if n >= 3:
        action = "REWRITE_PARAGRAPH"   # 3 o más marcadores = señal. Reescribe el párrafo, no palabra por palabra.
    elif always:
        action = "REPLACE"             # un puente de revelación / paralelismo negativo / marcador de sinceridad se limpia siempre,
                                       # aunque comparta párrafo con un marcador común (se evalúa ANTES de n == 2)
    elif n == 2:
        action = "FLAG_ONLY"           # 2 = zona gris. Infórmalo y deja las palabras: la auditoría admite 0-2 por unidad.
    else:
        action = "LEAVE"               # una palabra común aislada no es un veredicto
    return {"hits": hits, "count": n, "action": action}
```

Reglas de aplicación:
- Puntúa los marcadores forenses por separado: una coincidencia = borrar, sin
  umbral de densidad.
- Los conteos por caption también importan en dos patrones: tríadas (3 o más
  por caption = limpiar hasta dejar la primera natural; una o dos tríadas
  naturales pasan, el mismo umbral que usa la auditoría) y fragmentos sueltos
  (3 o más por caption = unirlos, ver Pasada 2).
- Nunca reemplaces una palabra por un sinónimo de la misma lista. "Potenciar"
  por "impulsar" no es una corrección.
- Cuando reescribas un párrafo, hazlo en el registro del autor (lo casual en
  minúscula sigue casual en minúscula, sus emojis se quedan), no en un registro
  "neutro". La sencillez a temperatura uniforme es en sí misma una huella.

---

## Nivel FORENSE (siempre activo)

Filtraciones reales del modelo que ningún humano escribe. Borrar o señalar en
cuanto aparecen.

| Patrón | Acción |
|---|---|
| `oaicite`, `contentReference`, `turn0search0`, `attached_file`, `grok_card` | borrar el marcador |
| "Según mi última actualización", "Hasta la fecha de mi conocimiento", "No puedo navegar por internet", "Como modelo de lenguaje", "Como IA" | borrar la línea del aviso |
| `[Tu nombre]`, `[Marca]`, `[inserta X aquí]`, `AAAA-MM-DD` espacios de plantilla sin completar | señalar y pedirle al usuario que los complete |
| Restos de traducción automática: frases en inglés sueltas en medio del texto en español, comillas o etiquetas sin traducir | señalar y corregir |
| Rayas por encima del límite (ver abajo) | reemplazar el exceso por coma, dos puntos, paréntesis o una reescritura; nunca por punto |

### Límite de rayas (aproximadamente 1 cada 100 palabras)

El carácter no es un indicio por sí solo. En inglés, según la versión original,
los modelos de 2026 usan menos rayas que los humanos y el 29% de los captions
humanos de su corpus tiene una. En español, además, la raya es normativa para
incisos (—así—) y diálogos. Prohibirla por completo esteriliza los captions.
Lo que sigue siendo forense es el hábito de pegar oraciones con rayas: 3 o más
en un caption corto.

Indicio específico del español: la **raya a la inglesa**, usada sola y sin raya
de cierre para unir dos oraciones ("Probé todo — nada funcionó"). En un inciso
correcto la raya abre y cierra, pegada a la palabra que sigue y a la que
precede: "Probé todo —y digo todo— antes de rendirme." Si una raya suelta une
dos oraciones, reemplázala por dos puntos, coma o punto y coma.

```python
def em_dash_excess(text: str) -> int:
    """Devuelve cuántas rayas superan el límite (~1 cada 100 palabras, mínimo 1, máximo 2 por caption).
    0 = no tocar ninguna raya. Una slide de carrusel cuenta como unidad propia con límite 1.
    Un par de rayas que abre y cierra un mismo inciso cuenta como 1."""
    words = len(text.split())
    cap = max(1, min(2, round(words / 100)))
    return max(0, count_dash_uses(text) - cap)

# Orden de reemplazo para las rayas EXCEDENTES (conserva la que más trabaja, normalmente la primera):
#   1. coma             si la raya une una cláusula a la oración principal
#   2. dos puntos       si la raya introduce una revelación, una lista o una consecuencia
#   3. paréntesis       si el par de rayas envuelve un inciso
#   4. salto de línea   propio de Instagram: el inciso va en su propia línea
#   5. reescritura      si nada de lo anterior se lee natural
# NUNCA punto. "X. Y." a partir de una raya partida crea fragmentos apilados, un indicio peor que la raya.
```

---

## Nivel ESTRICTO (activo por defecto)

Lo que señalan los lectores humanos expertos cuando detectan texto de IA
(vocabulario 53%, estructura de oraciones 36%, según los estudios en inglés de
la versión original). Todas las listas de vocabulario y gramática pasan por
`score_paragraph()`; los puentes de revelación, los paralelismos negativos y los
marcadores de sinceridad se limpian con una sola aparición.

### Puntuación

- Comillas tipográficas inglesas ("…") -> comillas rectas ("") o latinas («»),
  según el Perfil de voz; sé coherente en todo el texto.
- `--` -> coma o salto de línea (no punto: aquí un punto apila fragmentos).
- Guion corto (`–`) entre oraciones -> coma. Los rangos numéricos (7-9) se quedan.
- Las rayas se manejan con `em_dash_excess()` de arriba, no se eliminan todas.
- Signos de apertura ausentes ("Qué opinas?", "Increíble!") -> agregar ¿ ¡.
- Exceso de signos de exclamación (¡¡¡!!! o más de 2 exclamaciones por caption)
  -> dejar como máximo una, salvo que sea la voz del autor.

### Vocabulario: marcadores en español (puntuados por densidad)

Palabras comunes que los modelos sobreseleccionan en español. Son español
normal, así que una por párrafo está bien. Tres en un párrafo son una firma.

| Marcador | Reemplazo preferido cuando el párrafo supera el umbral |
|---|---|
| significativo, notable | un número ("31% más guardados", no "un crecimiento significativo"; pregunta si no hay ninguno) |
| crucial, fundamental, esencial, vital, clave | borrar, o decir por qué importa |
| cabe destacar, es importante destacar, vale la pena mencionar | borrar |
| integral, holístico | completo |
| insights, aprendizajes clave | decir qué se aprendió |
| robusto | sólido (mantener si es término técnico) |
| aprovechar al máximo | usar |
| fomentar | armar, crear |
| panorama, ecosistema, universo | el campo, el sector, o nombrarlo |
| matizado | concreto |
| multifacético | borrar |
| optimizar | simplificar, mejorar (decir qué) |
| potenciar, impulsar, catapultar, elevar | subir, mejorar (decir cuánto) |
| empoderar | ayudar |
| desbloquear | abrir, conseguir |
| navegar (en sentido figurado) | manejar |
| sumergirse, adentrarse, explorar (figurado) | entrar en, ver |
| sin fisuras, fluido | sin problemas |
| transformar, revolucionar | cambiar (decir qué) |
| innovador, disruptivo, poderoso, increíble | borrar o mostrar el dato |

Adverbios y conectores de relleno (cada uno cuenta como un marcador; borrar
cuando se supera el umbral): fundamentalmente, esencialmente, en definitiva, en
última instancia, sin lugar a dudas, sin duda alguna, ciertamente,
indudablemente, asimismo, por otro lado, en resumen, además (cuando abre cada
párrafo).

### Marcadores gramaticales (puntuados por densidad; la firma estructural)

```python
GRAMMAR_MARKERS = {
    # Aperturas con gerundio: "Aprovechando nuestros datos, logramos..." / "Partiendo de esto, ..."
    "gerund_opener": r"(?m)^[\s>*\-]*\w+(ando|iendo|yendo)\b[^.]{0,60},",
    # Gerundio de posterioridad al final de la oración (uso discutido y muy típico de IA):
    # "Lanzamos la función, logrando así un 30% más de retención."
    "gerund_tail": r",\s+\w+(ando|iendo|yendo)\b(\s+así)?\s",
    # Cadenas de nominalizaciones que esconden al actor: "la implementación de la optimización de"
    "nominalisation": r"\b(la|el|los|las) \w+(ción|sión|miento|mientos|ización|encia|anza) de (la|el|los|las) \w+(ción|sión|miento|ización|encia)\b",
    # Sustantivos abstractos apilados
    "abstract_stack": r"\b(sinergia|transformación|optimización|innovación|eficiencia|escalabilidad|crecimiento|impacto)\b.{0,40}\b(sinergia|transformación|optimización|innovación|eficiencia|escalabilidad|crecimiento|impacto)\b",
}
# Corrección de gerund_opener: el actor primero. "Aprovechando nuestros datos, bajamos la tasa de bajas" -> "bajamos la tasa de bajas con nuestros datos."
# Corrección de gerund_tail: separa en dos verbos conjugados. "..., logrando así un 30% más" -> "... y la retención subió un 30%."
# Corrección de nominalisation: usa el verbo. "la implementación del nuevo flujo" -> "cuando lanzamos el nuevo flujo"
```

### Capa de modismos de modelo (puntuados por densidad)

Frases que funcionan como muletillas de modelo en captions en español, muchas
calcadas del inglés. Cada una cuenta como un marcador; "léelo de nuevo" y "esa
es la verdadera historia" se limpian con una sola aparición como cierres.

```python
IDIOM_LAYER_ES = [
    r"\b(silenciosamente|en silencio)\b",          # calco de "quietly shipped"
    r"(?m)^\w+ importa\.$",                        # "la constancia importa." como línea suelta
    r"\b(efecto|interés) compuesto\b",             # en sentido figurado
    r"\buna señal\b|\bla señal\b",
    r"\bhacer el trabajo\b",
    r"\b(léelo|leelo) (de nuevo|otra vez)\b|\brelee eso\b",
    r"\besa es la (verdadera|real) historia\b",
    r"\benergía de protagonista\b",
    r"\by eso lo cambia todo\b",
    r"\besto es oro\b",
    r"\bel secreto (mejor guardado|que nadie te cuenta)\b",
    r"\bspoiler:\s",
]
```

### Puentes de revelación (una aparición = reemplazar)

```python
REVEAL_BRIDGES = [
    (r"(?im)^¿?(el|la) (resultado|respuesta|lección|trampa|clave|verdad|sorpresa)\?\s*", ""),   # "¿El resultado?"
    (r"(?i)\bno es (solo |solamente )?\w[^,.]{0,40}, es \b", None),                           # "No es solo X, es Y" (reescribir como dos afirmaciones)
    (r"(?i)^deja de \w[^,.]{0,40}[.,] empieza a \b", None),                                    # "Deja de X, empieza a Y"
    (r"(?im)^(te cuento|esto es|así es) (lo que|cómo|por qué)\b[^:.\n]{0,40}[:.]\s*", ""),     # "Te cuento lo que..", "Así es cómo.."
    (r"(?im)^(giro (inesperado|de guion)|spoiler|alerta de spoiler)[:?]\s*", ""),
    (r"(?im)^hablemos (de|sobre)\b[^.\n]{0,40}[.:]\s*", ""),                                  # apertura "Hablemos de.."
    (r"(?im)^(y aquí viene lo mejor|pero aquí está el truco|y adivina qué)[:.]?\s*", ""),
]
# Corrección: borra el puente y deja que la oración siguiente se sostenga sola. De todos modos era el punto.
```

### Paralelismo negativo (una aparición = reescribir)

Quita las construcciones "no X, sino Y" / "no se trata de X, se trata de Y" y
todas sus variantes ("La pregunta no es X, es Y", "Esto no es X. Esto es Y.",
"No solo X, sino también Y" usada como gancho). Reescribe como dos afirmaciones
sin depender de una sustitución automática, y señálalo al usuario porque
conservar el significado requiere criterio. En el corpus de la versión original
ningún caption humano usaba esta forma.

### Regla de tres (estricta por densidad; se permite una tríada natural)

En inglés, los modelos de 2026 usan tricolon al doble de la tasa humana experta,
y el 23% de los captions humanos del corpus tiene uno. El indicio es la tríada
apilada o perfectamente paralela, la hueca y la repetida, no la forma.

```python
NO_NO_SOLO = r"\b(sin \w+)[,.] (sin \w+)[,.] ((?:solo|sólo|solamente) \w+)"   # "Sin X. Sin Y. Solo Z." / "sin X, sin Y, solo Z"

def detect_triads(text: str) -> list:
    patterns = [
        r"(\w+), (\w+),? (?:y|e) (\w+)",                    # tríos de palabras
        r"(\w+ \w+), (\w+ \w+),? (?:y|e) (\w+ \w+)",        # tríos de frases cortas
        r"(?m)^(\w+)\. (\w+)\. (\w+)\.$",                   # "Simple. Efectivo. Fácil." (también un indicio de la Pasada 2)
        NO_NO_SOLO,                                         # construcción escenificada, nunca una tríada natural
    ]
    return [m for p in patterns for m in re.finditer(p, text, flags=re.I)]

HOLLOW_ADJECTIVES = {"dinámico", "dinámica", "innovador", "innovadora", "rápido", "barato", "mejor", "simple",
                     "efectivo", "efectiva", "fácil", "audaz", "claro", "clara", "enfocado", "escalable",
                     "poderoso", "poderosa", "estético", "auténtico", "auténtica"}
ABSTRACT_NOUNS = {"crecimiento", "impacto", "valor", "innovación", "eficiencia", "resultados", "éxito",
                  "claridad", "libertad", "escala", "impulso", "constancia", "mentalidad", "estrategia",
                  "visión", "propósito", "pasión"}

def hollow(t: "re.Match", text: str) -> bool:
    """Una tríada es hueca cuando sus elementos son intercambiables: todos son adjetivos o sustantivos
    abstractos y ninguno trae un respaldo (un nombre propio, un número, un $ o %). Igual cantidad de palabras
    NO es un indicio por sí sola: "facturas de Stripe, registros de Vercel y alertas de GitHub" es una
    tríada concreta natural. La mayúscula por sí sola nunca es un respaldo: la mayúscula que abre una oración
    ("Simple, efectivo y fácil") es mayúscula inicial, no un nombre. Un nombre es una mayúscula que NO abre oración."""
    def opens_sentence(pos: int) -> bool:
        return re.search(r"(?:^|[.!?¿¡\n])\s*$", text[:pos]) is not None
    def has_receipt() -> bool:
        for g in range(1, t.lastindex + 1):
            pos = t.start(g)
            for w in t.group(g).split():
                if re.search(r"[0-9$%€]", w):
                    return True
                if w[:1].isupper() and not opens_sentence(pos):
                    return True
                pos += len(w) + 1
        return False
    items = t.groups()
    all_abstract = all(x.lower().strip() in HOLLOW_ADJECTIVES or x.lower().strip() in ABSTRACT_NOUNS
                       or x.lower().split()[-1] in ABSTRACT_NOUNS for x in items)
    return (not has_receipt()) and all_abstract

def triad_action(triads: list, text: str) -> list:
    """Se llama una vez por caption con sus tríadas (de detect_triads(text)). Limpia de inmediato toda tríada
    hueca. Las tríadas naturales (concretas, no intercambiables) se deciden por densidad, con el MISMO umbral
    que la auditoría: una o dos pasan; con 3 o más en el caption se limpia hasta dejar la PRIMERA natural.
    El modo reescritura nunca es más duro que el modo auditoría. El umbral es por caption."""
    actions = []
    over_density = len(triads) >= 3
    kept_one = False
    for t in triads:
        staged = t.re.pattern == NO_NO_SOLO          # "sin X, sin Y, solo Z" es escenificado con cualquier puntuación, siempre se reescribe
        if hollow(t, text) or staged or (over_density and kept_one):
            actions.append((t, "REWRITE_AS_TWO_OR_FOUR"))   # 2 elementos, o 4 con uno que rompa el patrón
        else:
            actions.append((t, "LEAVE"))
            kept_one = True
    return actions
```

### Frases muertas (borrar o reescribir)

- "en el mundo acelerado de hoy", "en la era digital", "en la era de la IA",
  "en un mundo cada vez más competitivo"
- "al final del día" (calco), "a fin de cuentas" como muletilla
- "un antes y un después", "cambia las reglas del juego", "llevarlo al
  siguiente nivel", "imprescindible", "cambio de paradigma", "análisis profundo"
- "el mundo de {cosa}" ("en el mundo del marketing")
- "la dura verdad es" / "la incómoda realidad es"
- "descubre el poder de", "desata tu potencial", "da el salto"

### Cierres muertos (reescribir como aterrizaje o pedido concreto)

- "¿Qué opinas?" / "¿Ustedes qué piensan?"
- "¿Opiniones?"
- "Doble toque si estás de acuerdo."
- "Etiqueta a 3 amigos que necesitan esto."
- "Comenta SÍ abajo."
- "Léelo de nuevo."
- "¡Espero que te sirva!" / "¡Déjamelo en los comentarios!"
- Una línea final de una sola palabra ("Todavía.")

Una invitación a guardar o enviar que nombra una razón ("guárdalo antes de tu
próximo post") no es un cierre muerto; es la llamada a la acción que Instagram
premia.

### Lluvias de emojis

- 4 o más emojis en un caption, o un emoji en cada línea: reducir a 0-3 ubicados
  con intención.
- La firma de emojis de IA de 2024-25 (cohete, destellos, fuego, 100, manos
  levantadas seguidos) se limpia con una sola aparición como conjunto.
- Los 1-3 emojis intencionales del autor son su voz y se quedan (ver Conservar).

## Calcos del inglés (activo por defecto)

Señales de que el texto se pensó en inglés y se tradujo, o de que el modelo
copió patrones del inglés. Cada uno cuenta como un marcador.

- **Mayúsculas de título en inglés:** "Cómo Crecer En Instagram Sin Gastar" ->
  "Cómo crecer en Instagram sin gastar". En español solo va con mayúscula la
  primera palabra y los nombres propios.
- **Falsos amigos y calcos léxicos:** "aplicar a un trabajo" (postularse),
  "remover" (quitar), "eventualmente" por "finalmente", "agresivo" por
  "ambicioso", "asumir" por "suponer", "librería" por "biblioteca" (de código),
  "hacer sentido" (tener sentido), "en orden a" (para), "estar supuesto a"
  (deber).
- **Estructuras calcadas:** "es por eso que" en cada párrafo; voz pasiva con
  "ser" donde el español usaría "se" ("el post fue publicado" -> "se publicó el
  post" o "publiqué el post"); posesivos innecesarios ("me lavé mis manos");
  "el mismo" como pronombre ("revisa el archivo y envía el mismo").
- **Puntuación a la inglesa:** solo signo de cierre en preguntas y
  exclamaciones, coma antes de "y" en enumeraciones simples (coma de Oxford).
- **Cifras a la inglesa:** "$4,200.50" en un texto que usa convención hispana.
  Usa la convención del Perfil de voz; por defecto, punto para miles y coma
  decimal.

## Limpiezas de formato de Instagram (siempre se aplican)

- Un gancho que necesita la línea 2 para entenderse: reescribir para que los
  primeros 125 caracteres se sostengan solos.
- 6 o más hashtags, o alguno a mitad de oración: reducir a un set dimensionado
  de 3-5 al final o en el primer comentario (ver
  `../../../references/hashtag-strategy.md`).
- Un título pelado en la slide 1 del carrusel: reescribir como promesa + bucle
  abierto.
- Un caption de más de 2.200 caracteres: ajustarlo.
- Texto sobre la imagen de las slides: como máximo una raya por slide, y solo si
  cumple una función real; las slides son cortas.

---

## Pasada 2 - Ritmo (solo protección contra la uniformidad)

Reemplaza el "ROMPER (forzar variación)" de V2. Los detectores no puntúan la
variación del ritmo (GPTZero lo abandonó en 2023). Los captions son de largo
medio y, en las plataformas con datos de interacción de la versión original, la
variación del largo de las oraciones es neutra o negativa, así que el ritmo no
es una palanca de alcance. Lo que sí notan los lectores es la uniformidad plana
de máquina (la estructura = 36% de los juicios expertos) y, peor aún, la
variación escenificada: la alternancia mecánica largo/corto es una huella
aprendible del humanizador. Entonces: corrige el ritmo solo donde suena plano,
quita la variación fabricada en todas partes y nunca agregues variación como
táctica.

```python
STACCATO_TELLS = [
    r"(?m)^\w+\.$",                                                   # línea de una palabra para dar dramatismo: "Todavía." "Exacto."
    r"(?m)^(\w+\. ){2,}\w+\.$",                                       # "Corto. Directo. Listo." / "Simple. Efectivo. Fácil."
    r"(?i)\bsin \w+\. sin \w+\. (solo|sólo|solamente) \w+",           # "Sin X. Sin Y. Solo Z."
    r"(?i)\btodo (el|lo) \w+\. nada (del|de lo) \w+",                 # "Todo el X. Nada del Y."
    r"(?im)^¿?(el|la) (resultado|respuesta|lección|trampa|clave|verdad)\?",  # revelación "¿El resultado?" (también puente estricto)
    r"(?i)¿(por qué|cómo|qué pasó)\? (porque|simple|fácil)\b",        # preguntas y respuestas pseudosocráticas
    r"(?i)\b(eso es todo|así de simple|punto|y punto|fin)\.$",
]

def is_standalone_fragment(s: str) -> bool:
    """Un fragmento es una línea corta sin sujeto + verbo conjugado: "Todavía.", "Exacto.", "Sin excusas.",
    "Todas y cada una de las veces." Una oración completa corta ("Funcionó.", "Subieron las ventas.") no es un
    fragmento y nunca cuenta para el límite; lo corto no es el indicio, el fragmento para dar dramatismo sí.
    Ojo: en español el sujeto puede ir tácito; "Funcionó." tiene verbo conjugado y es oración completa."""
    return len(s.split()) < 4 and not has_finite_verb(s)

def restore_rhythm(text: str) -> str:
    """V3. Quita la variación escenificada; desaplana solo lo que suena plano como máquina. Nunca fabrica variación."""
    paragraphs = split_paragraphs(text)
    fragments_seen = 0

    for i, p in enumerate(paragraphs):
        # 1. Primero elimina el ritmo escenificado. Une las ráfagas entrecortadas en una oración completa con una cláusula real.
        for pat in STACCATO_TELLS:
            if re.search(pat, p):
                p = merge_into_sentence(p, pat)     # "Sin filtros. Sin presets. Solo luz." -> "sin filtros ni presets, solo la luz de la ventana."

        sents = split_sentences(p)
        lengths = [len(s.split()) for s in sents]

        # 2. Limita los fragmentos sueltos a 2 por CAPTION, no por párrafo. Solo cuentan los fragmentos reales;
        #    "Funcionó. Subieron las ventas. Volvieron los clientes." son tres oraciones cortas, no tres fragmentos.
        for j, s in enumerate(sents):
            if is_standalone_fragment(s):
                fragments_seen += 1
                if fragments_seen > 2:
                    sents[j] = attach_to_neighbor(sents, j)   # intégralo a la oración anterior con coma o dos puntos

        # 3. Desaplana SOLO un párrafo plano como máquina: 4 o más oraciones, todas a +-3 palabras de la media,
        #    sin ninguna cláusula subordinada. Entonces extiende la ÚNICA oración con más contenido uniéndola a su
        #    vecina natural con una cláusula que trabaje (porque / que / cuando / después de que), no con una coma
        #    suelta. Una vez por párrafo, y solo si el resultado suena al autor. Un párrafo con una oración larga y
        #    una corta ya está bien.
        if len(sents) >= 4 and all(abs(n - mean(lengths)) <= 3 for n in lengths) and not any(has_working_clause(s) for s in sents):
            k = max(range(len(sents)), key=lambda j: lengths[j])
            j = k + 1 if k + 1 < len(sents) else k - 1
            sents[k] = join_with_clause(sents[k], sents[j])
            del sents[j]                              # se quita la vecina absorbida para que nada aparezca dos veces

        # 4. Nunca largo/corto/largo/corto. Si el párrafo ahora alterna (4 o más oraciones que van y vienen entre
        #    cortas de <8 palabras y largas de >=16), integra la SEGUNDA oración corta a la anterior.
        #    El vaivén es la huella del humanizador.
        lengths = [len(s.split()) for s in sents]
        if len(lengths) >= 4 and all((lengths[k] < 8) != (lengths[k + 1] < 8) for k in range(len(lengths) - 1)) \
                and all(n < 8 or n >= 16 for n in lengths):
            k = [j for j, n in enumerate(lengths) if n < 8][1]
            sents[k - 1] = join_with_clause(sents[k - 1], sents[k])
            del sents[k]

        # 5. Captions de una idea por línea (cada párrafo una oración) y slides de carrusel: no tocar el ritmo.

        paragraphs[i] = rejoin_keeping_breaks(p, sents)   # vuelve a poner los saltos de línea propios del párrafo; la pasada edita oraciones, nunca saltos

    return "\n\n".join(paragraphs)
```

Diagramación frente a ritmo: las líneas de una oración con líneas en blanco
entre ellas son la diagramación nativa de un caption de Instagram y esta pasada
**no** las toca. "Hice crecer una cuenta de 0 a 10.000 en 4 meses." en su propia
línea es diagramación. "Todavía." en su propia línea es fragmento para dar
dramatismo. La pasada edita oraciones, nunca los saltos de línea.

## Pasada 3 - Inserciones prohibidas (marcadores de sinceridad, atenuantes)

La Pasada 3 solo agrega concreción (un número de precisión poco redonda con
referente, una entidad con nombre, un hecho fechado dicho sin rodeos). Nunca
agrega lo siguiente, y la Pasada 1 estricta lo quita cuando el borrador ya lo
tiene como apertura o giro:

```python
SINCERITY_MARKERS = [
    # Anclado al inicio de línea O a un límite de oración, para atrapar también un giro en la misma línea
    # ("El lanzamiento falló. Hablemos claro, esto dolió.").
    r"(?im)(?:^|(?<=[.!?]\s))(seamos (sinceros|honestos|claros)|te voy a ser (sincero|sincera|honesto|honesta)|voy a ser (sincero|sincera|honesto|honesta|directo|directa)|¿honestamente\?|la versión honesta (es)?|para ser (directo|directa|honesto|honesta|justo|justa|transparente)|hablemos claro|con total transparencia|¿puedo ser (sincero|sincera|vulnerable)\?|voy a decir lo que nadie dice|no te voy a mentir|no voy a mentir|opinión impopular|hora del cuento|storytime)[:,.]?\s*",
    r"(?im)(?:^|(?<=[.!?]\s))pov:\s*(?!.*\b(tú|tu|te|ti|vos|usted)\b)",   # "POV:" sobre algo que no es un punto de vista
    r"(?i)\b(puede que me equivoque,? pero|quizás|tal vez|pareciera que|me parece que|en mi humilde opinión|creo que es justo decir)\b",  # atenuantes insertados: limpiar solo si NO están en las muestras de voz del autor
]
# Corrección: borra el marcador y deja la oración que sigue. Si esa oración no es un hecho concreto,
# el marcador estaba haciendo el trabajo de la vulnerabilidad. Pídele el hecho al autor.
# Evidencia (estudios en inglés): la duda actuada es el doble de común en texto de IA que en texto humano experto;
# la "falsa vulnerabilidad" es un indicio con nombre en 2026. La regla: nunca fabricar una, y nunca envolver un hecho en una.
```

## Conservar esto (voz del usuario, no limpiar)

- El registro casual en minúscula si así escribe el usuario
- `..` como pausa suave y los saltos de línea simples como tramos
- Uno o dos fragmentos usados a propósito ("siempre.") - el límite es 2 por
  caption, no 0
- Una raya cada ~100 palabras, y los incisos bien abiertos y cerrados con raya.
  No lleves la cantidad a cero
- Una enumeración natural de tres con elementos concretos y no intercambiables
- Una oración realmente larga por párrafo, aunque una guía de estilo la partiría
- Los 1-3 emojis intencionales del autor
- Su variante de español (tuteo, voseo o usted), sus regionalismos deliberados y
  su forma de saludar o despedirse
- Coloquialismos naturales del autor ("igual", "o sea", "la verdad") cuando
  aparecen en sus muestras de voz
- Números concretos con referentes y entidades con nombre (agrega MÁS, nunca quites)
- Detalles sensoriales en primera persona
- Las reacciones y opiniones del autor, incluso una tajante. Un tono plano en
  todo el caption es una huella del humanizador
- Un único marcador común en un párrafo ("fundamental", "robusto" como término
  técnico). Uno no es un veredicto
- Su historia real. Nunca inventes un detalle para que un caption funcione
