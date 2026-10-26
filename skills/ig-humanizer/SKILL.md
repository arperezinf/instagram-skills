---
name: ig-humanizer
description: "Quita de un caption o slide de Instagram en español los indicios de IA que notan los lectores: vocabulario inflado por densidad, puentes de revelación, ráfagas entrecortadas, tríadas apiladas, sinceridad actuada, lluvias de emojis, calcos del inglés; limita las rayas. Incluye --mode audit y --mode profile. No promete engañar detectores. No para escribir desde cero (usa ig-caption-writer o ig-carousel-planner). Claves: humanizar, auditar."
---

# Humanizador para Instagram V3 (español)

Reescribe un caption o el texto de las slides de un carrusel para quitar los
indicios de IA que notan los lectores humanos, y audita un caption terminado
contra la lista de verificación de Instagram 2026. Trabaja sobre texto en
español; si recibe texto en inglés, avisa y pregunta si debe traducirlo o
humanizarlo en su idioma original.

La versión original de esta skill se basó en la taxonomía "Signs of AI writing"
de Wikipedia, la literatura de estilometría 2025-2026, un corpus propio de
captions de Instagram en inglés (n=284, solo prevalencia) y patrones propios de
Instagram (el corte de 125 caracteres, el registro casual en minúscula, los
hashtags dimensionados, la estructura de envíos y guardados).
**V3 (2026-09):** recalibrada con evidencia de 2026. El vocabulario se puntúa
por densidad, las rayas se limitan en lugar de prohibirse, el ritmo forzado
pasa a ser un indicio en lugar de una solución y hay una protección contra la
sobrecorrección.

**Sobre los datos:** las cifras citadas abajo (porcentajes, tasas por 1.000
palabras) provienen de estudios y de un corpus **en inglés**. No hay en este
paquete una medición equivalente para el español. Los catálogos de marcadores
en español de esta versión son una adaptación por criterio lingüístico, no una
medición: trátalos como guía, no como estadística.

**Lo que esta skill no hace:** no hace que un texto "pase" GPTZero, Pangram,
Turnitin u Originality. Son clasificadores entrenados sobre la firma de estilo
del ajuste por instrucciones; según los estudios citados por la versión
original, las reescrituras del tipo "que suene como una persona real" se
detectan el 92-95% de las veces, y las reescrituras mecánicas leves aumentan la
detectabilidad. En textos del largo de un caption (menos de 300 palabras) los
puntajes de los detectores son ruido. El valor real está en otro lado: los
lectores expertos señalan el vocabulario (53%) y la estructura de las oraciones
(36%) como lo que delata un texto de IA, y en Instagram un caption que suena a
cuenta de marca no consigue ni el guardado ni el envío. Esta skill quita lo que
notan esos lectores.

## Qué cambió en V3

Nivel de evidencia entre corchetes (referido a los estudios en inglés de la
versión original): [fuerte] = replicado en 2 o más estudios independientes de
2025-2026 o en el corpus propio; [proveedor] = conjunto de datos de una sola
plataforma o proveedor; [débil] = un solo estudio o informe de panel de expertos.

- **El vocabulario pasó de una lista de borrado a una puntuación por densidad.**
  En inglés, las palabras de 2023-24 (delve, tapestry, realm) están en declive
  [fuerte] y los marcadores duraderos son palabras comunes más gramática:
  nominalizaciones y aperturas con gerundio [fuerte]. En español el equivalente
  son verbos y adjetivos inflados (potenciar, fundamental, crucial), conectores
  de relleno (cabe destacar, en definitiva) y gramática: cadenas de
  nominalizaciones y gerundios encadenados al final de la oración ("…, logrando
  así un mayor impacto"). Un marcador en un párrafo no es un veredicto. Tres sí.
- **La raya no es un indicio por sí sola.** En inglés los modelos de 2026 la
  usan menos que los humanos y el 29% de los captions humanos del corpus tiene
  una [fuerte]. En español la raya tiene usos normativos (incisos y diálogos),
  así que con más razón no se prohíbe. Lo que sí delata es el **uso a la
  inglesa**: una raya suelta pegada a las palabras para unir dos oraciones, sin
  raya de cierre en un inciso. Regla: limitar a aproximadamente 1 cada 100
  palabras (1-2 por caption) y reemplazar solo el exceso por coma, dos puntos,
  paréntesis o una reescritura. Nunca por punto. Cero rayas en un caption largo
  también puede ser un indicio.
- **El ritmo forzado es el indicio número 1 de 2026, no la solución.** La
  alternancia mecánica largo/corto es una huella aprendible de los humanizadores
  [débil], y "Corto. Directo. Listo.", "Sin X. Sin Y. Solo Z.", líneas de una
  palabra para dar dramatismo y revelaciones del tipo "¿El resultado?" son hoy
  los indicios que más citan los lectores [fuerte]. Los captions son de largo
  medio, así que la Pasada 2 solo protege contra la uniformidad: corrige un
  párrafo que suene plano como máquina, nunca fabriques variación.
- **La regla de tres sigue siendo un indicio, por densidad.** Los modelos de
  2026 usan tricolon al doble de la tasa humana experta [fuerte], y el 23% de
  los captions humanos del corpus tiene uno [fuerte]. Una enumeración natural de
  tres con elementos concretos se queda. Las tríadas apiladas, perfectamente
  paralelas o huecas, y una tercera tríada en un caption, se limpian.
- **Inyectar huellas humanas estaba a medias mal.** Las entidades con nombre y
  lo concreto funcionan [fuerte]; un número de precisión poco redonda con un
  referente en los primeros 125 caracteres es el gancho más fuerte. Los números
  pelados no distinguen, y los atenuantes y confesiones insertados son
  contraproducentes: la duda actuada es el doble de común en texto de IA, y los
  anuncios de sinceridad ("seamos sinceros", "hablemos claro", "POV:" sobre algo
  que no es un punto de vista) son un indicio con nombre en 2026 [fuerte]. La
  Pasada 3 pide en cambio un hecho incómodo, fechado y dicho sin rodeos.
- **Protección contra la sobrecorrección.** El texto de un humanizador tiene su
  propia huella [débil]. La Pasada 4 verifica si las pasadas 1-3 introdujeron
  justo los patrones que debían quitar. Las ediciones son proporcionales a los
  problemas reales. Ante la duda, deja el texto como está.

## Idioma

- Escribe el contenido y tus respuestas al usuario en **español neutro**, con
  tuteo y sin regionalismos ni voseo.
- No deduzcas otra variante por el país, la ciudad o el público que mencione el
  usuario. Que diga "mi cuenta es de Argentina", "vivo en Madrid" o "mi público
  es mexicano" NO cambia la variante: sigues con tuteo neutro ("busca", "revisa",
  "quieres", nunca "buscá", "revisá", "querés"). El país solo orienta el contenido
  (hashtags locales, referencias, horarios).
- Cambia la variante solo si el Perfil de voz (`../../references/voice-profile.md`)
  lo indica o si el usuario lo pide explícitamente ("háblame de vos", "escríbelo
  en español de España").
- Ortografía completa (tildes, ¿ ¡) y sin calcos del inglés.

## Cuándo usarla

- Antes de publicar cualquier caption o carrusel redactado con IA (modo reescritura)
- Revisión previa a publicar de un caption terminado (modo auditoría, ver `sub-skills/post-audit.md`)
- Cuando un caption suena raro y no logras precisar por qué

## Entrada

Cualquier texto: un caption, el texto sobre la imagen de un carrusel o el
caption de un reel. Opcional: muestras de la voz objetivo (captions anteriores
del usuario).

## Salida

- Texto reescrito sin los indicios de IA
- Un diff que muestra qué cambió y por qué
- Cantidad de caracteres del caption (señalando si el gancho pasa de los primeros 125)
- Densidad de indicios por párrafo (marcadores por párrafo; 3 o más dispararon una reescritura)
- Confianza de lectura: "se lee humano", "mixto", "se lee IA" (una estimación
  según los indicios que nota un lector, no un puntaje de detector)

## Modos

```bash
# Por defecto: limpia indicios de IA (forense + estricto) y corrige problemas de formato de Instagram
ig-humanizer <texto>

# Solo forense: intervención mínima, solo elimina filtraciones del modelo
ig-humanizer --mode forensic <texto>

# Auditoría: revisión de aprobado/reprobado, solo detecta, no reescribe
# Aplica la lista de Instagram 2026: gancho de 125 caracteres, largo del caption,
# hashtags dimensionados, límite de emojis, calidad de la llamada a la acción,
# recordatorio de contenido multimedia.
# Devuelve Bloqueantes + Advertencias + correcciones sugeridas. Ver sub-skills/post-audit.md.
ig-humanizer --mode audit <texto>

# Perfil: crea/actualiza el Perfil de voz y marca del usuario. Ver la sección de abajo.
ig-humanizer --mode profile
```

## Las cuatro pasadas

### Pasada 1 - LIMPIAR (puntuar, luego borrar o reemplazar)

Aplica los catálogos por niveles de `references/scrub-rules.md`. La unidad de
juicio es el **párrafo (o la slide), no la palabra**: cuenta marcadores por
párrafo, reescribe el párrafo con 3 o más y deja un marcador aislado salvo que
sea un puente de revelación, un paralelismo negativo, un marcador de sinceridad
o una filtración forense.

- **Forense** (siempre activo): filtraciones reales del modelo que ningún humano
  escribe. Marcadores de herramientas de IA (oaicite, contentReference,
  turn0search0), avisos de fecha de corte ("Según mi última actualización",
  "Como modelo de lenguaje"), espacios de plantilla sin completar ([Tu nombre]) y
  rayas por encima del límite (más de aproximadamente 1 cada 100 palabras).
- **Estricto** (activo por defecto): lo que notan los lectores. El vocabulario
  inflado puntuado por densidad (potenciar, impulsar, optimizar, fomentar,
  crucial, fundamental, esencial, clave, significativo, robusto, panorama,
  ecosistema, cabe destacar, en definitiva), marcadores gramaticales (cadenas de
  nominalizaciones, gerundios encadenados al final de la oración), la capa de
  modismos de modelo ("X importa.", "y eso lo cambia todo", "léelo de nuevo",
  "esto es oro"), puentes de revelación con una sola aparición ("¿El
  resultado?", "Te cuento lo que", "Deja de X, empieza a Y", "giro
  inesperado:"), todas las formas de paralelismo negativo ("No es solo X, es
  Y", "No se trata de X sino de Y"), tríadas apiladas o perfectamente paralelas
  y cualquier tercera tríada en un caption, frases hechas ("en el mundo
  acelerado de hoy", "un antes y un después", "llevarlo al siguiente nivel",
  "sumérgete en"), lluvias de emojis y cierres muertos ("¿qué opinas?", "doble
  toque si estás de acuerdo").
- **Calcos del inglés** (activo por defecto): Mayúscula En Cada Palabra De Un
  Título, signos de apertura ausentes (¿ ¡), comillas o puntuación a la inglesa,
  estructuras traducidas ("es por eso que" en cada párrafo, "en orden a",
  "hacer sentido", "aplicar a un trabajo").
- **Formato de Instagram** (siempre se aplica): gancho de 125 caracteres que se
  entiende solo, hashtags dimensionados, límite de emojis, promesa en la slide 1
  del carrusel, largo del caption.

### Pasada 2 - RITMO (solo protección contra la uniformidad)

Los detectores no puntúan la variación del ritmo, y los captions son de largo
medio (la mediana del corpus original está muy por debajo de las 200 palabras),
así que el ritmo no es ni una palanca de alcance ni una solución. Lo que notan
los lectores es la uniformidad mecánica (todas las líneas del mismo largo,
planas como máquina) y, peor aún, la variación escenificada que agregan los
humanizadores de segunda generación. Por eso la Pasada 2 tiene dos tareas:
corregir el ritmo solo donde suena plano como máquina y quitar la variación
fabricada en todas partes. Nunca agrega variación como táctica.

- Por párrafo: una oración realmente larga junto a una corta está bien y es como
  se ve la variación humana. Dos o tres oraciones de largo medio seguidas
  también están bien. Edita solo cuando todas las oraciones del párrafo tienen
  el mismo largo y suenan planas, y entonces edita una oración, no el párrafo.
- Fragmentos sueltos: como máximo 2 por caption en total. "siempre." una vez es
  una marca de voz. Tres en un caption son un patrón.
- Prohibidos directamente (reescribir como oraciones completas): revelaciones
  "¿El X? Y."; "Sin X. Sin Y. Solo Z."; "Todo el X. Nada del Y."; series de
  adjetivos "Simple. Efectivo. Fácil."; líneas de una palabra para dar
  dramatismo ("Todavía." "Exacto."); preguntas y respuestas pseudosocráticas
  ("¿Por qué? Porque..."); ráfagas "Corto. Directo. Listo.". Las series de
  fragmentos son el indicio.
- La diagramación no es ritmo. Una idea por línea con líneas en blanco entre
  ellas es el formato nativo de un caption y se queda. Lo que delata es el
  fragmento para dar dramatismo dentro de esas líneas. Mantén la diagramación,
  corrige las oraciones.
- El texto de las slides es corto por diseño; nunca cortes ni rellenes una slide
  por ritmo. Nunca alternes largo/corto/largo/corto entre slides o líneas. Ese
  vaivén es la huella del humanizador.

La verificación es "¿algún párrafo suena plano como máquina, y agregué un patrón
entrecortado?", no un número de variación.

### Pasada 3 - AGREGAR (huellas humanas)

Exígelas donde el contenido lo permita:
- Un número de precisión poco redonda CON un referente nombrado: quién, qué,
  cuándo o cuánto costó ("de 0 a 10.000 en 4 meses, publicando 3 veces por
  semana", no "creció rápido" ni "10.000"). Un número pelado no es una huella;
  la señal la lleva el referente.
- Una entidad con nombre (persona real, marca, fecha, herramienta)
- Un detalle concreto en primera persona (lo que viste, lo que costó, lo que se
  rompió)
- Un hecho concreto, fechado e incómodo dicho sin rodeos, sin una oración que lo
  enmarque antes ni después. No "hablemos claro, esto dolió: perdí al cliente".
  Solo "Perdí a mi cliente más grande el 14 de febrero." El hecho lleva la
  vulnerabilidad. El marco la convierte en sinceridad actuada, que los lectores
  hoy leen como indicio.
- El registro casual en minúscula si la voz lo pide

Prohibidos como apertura o giro (anuncios de sinceridad, un indicio con nombre
en 2026): "seamos sinceros", "te voy a ser honesto", "¿honestamente?", "para
ser directo", "la versión honesta es", "hablemos claro", "no te voy a mentir",
"¿me permites ser vulnerable un segundo?", "opinión impopular:" como prefacio de
una opinión popular, "POV:" sobre algo que no es un punto de vista. También
prohibidos como inserción: atenuantes que el autor no escribió ("quizás",
"puede que me equivoque, pero", "pareciera que"). La duda actuada es el doble
de común en texto de IA que en texto humano experto; agregarla hace que el
borrador suene más a IA, no menos.

Si la entrada no tiene esto, pídele al usuario un número, un nombre o un
momento. No inventes.

### Pasada 4 - AUTORREVISIÓN (protección contra la sobrecorrección)

El texto de un humanizador tiene su propia huella. Antes de devolverlo, relee el
resultado una vez y responde tres preguntas:

(a) ¿La Pasada 2 creó ráfagas entrecortadas, puentes de revelación del tipo
    "¿El resultado?", líneas de una palabra o un vaivén largo/corto/largo/corto?
    Si es así, une los fragmentos en oraciones completas.
(b) ¿La Pasada 3 agregó una confesión enmarcada, un anuncio de sinceridad o un
    atenuante que el autor nunca escribió? Si es así, quita el marco y deja solo
    el hecho, o elimina la inserción.
(c) ¿La limpieza aplanó la voz del autor: tono uniforme, sin reacción, sin
    detalles concretos, todas las rayas quitadas, todas las tríadas quitadas,
    todos los emojis quitados de una voz que los usa, el registro en minúscula
    pasado a mayúscula? Si es así, restaura lo que tenía el autor. Cero rayas y
    cero tríadas en un caption largo es un indicio en sí mismo.

Si alguna respuesta es sí, retrocede en lugar de limpiar más fuerte. Las
ediciones deben ser proporcionales a los problemas reales: un caption limpio
recibe dos o tres retoques, no una cuota. Ante la duda sobre si un patrón es del
autor o del modelo, déjalo.

## Reglas innegociables

Reglas de voz globales: ver la sección de reglas de voz del `SKILL.md` raíz.
Reglas adicionales propias de esta skill (V3):

- **La limpieza siempre corresponde.** Cuando te pidan humanizar, quitar la IA,
  terminar o publicar un caption, aplica al menos las pasadas forense +
  estricta antes de que salga. Vale aunque el usuario haya escrito el borrador,
  diga que le encanta tal como está o esté apurado. Quién es el autor, "ya está
  bien" y la prisa nunca son razones para saltarse la limpieza. La pasada
  forense + estricta no cambia el significado y lleva segundos: aplícala y
  luego publica. Si una restricción realmente prohíbe tocar el texto, dilo
  explícitamente y nombra cada indicio que queda; lo predeterminado es limpiar,
  no dejarlo pasar.
- **Limpia en proporción.** Una pasada que no encuentra nada no cambia nada. No
  inventes ediciones para justificar la ejecución y no informes un puntaje de
  detector como resultado; informa los indicios encontrados y corregidos.
- Conserva la afirmación y el significado reales del usuario. "Conservar su voz"
  abarca sus particularidades y lo que afirma, NO los puentes de revelación, las
  ráfagas entrecortadas ni un párrafo con 3 o más marcadores de vocabulario.
  Quitarlos no es cambiar su voz; es el trabajo.
- Nunca introduzcas hechos que no estaban en la entrada. Si falta un número,
  pregunta.
- Nunca introduzcas marcadores de sinceridad, atenuantes ni marcos
  confesionales. Si el borrador necesita un momento vulnerable, pide un hecho
  fechado y dilo sin rodeos.
- Conserva las particularidades de voz del usuario (inicios en minúscula,
  pausas suaves con `..`, una raya cada ~100 palabras, una tríada natural, sus
  1-3 emojis intencionales, su variante de español y su forma de tratamiento).
- Corrige la ortografía (tildes, ¿ ¡) salvo que el Perfil de voz indique que la
  omisión es deliberada.
- Nunca prometas resultados frente a detectores. Si el usuario pregunta "¿esto
  pasa GPTZero?", responde con honestidad: nadie puede prometerlo, y el puntaje
  en un caption de 150 palabras es ruido.
- Respeta la superficie: no conviertas el texto de las slides de un carrusel en
  un único caption ni al revés sin señalarlo.
- Nunca presentes un caption como listo para publicar sin el recordatorio de
  contenido multimedia (Instagram necesita una imagen o un video).

## Indicios propios de Instagram que detecta esta skill

- Un gancho que necesita la segunda línea para entenderse (el corte de "más" se
  lo come).
- Un caption que abre con "Hablemos de..", "Te cuento algo.." o "POV:" sobre
  algo que no es un punto de vista.
- 20-30 hashtags amontonados arriba en lugar de un set dimensionado de 3-5.
- Emojis espolvoreados en cada línea (4 o más por caption).
- Un título pelado en la slide 1 del carrusel en lugar de una promesa + bucle.
- Listas de tres apiladas o huecas ("más rápido, más barato, mejor"); una
  enumeración natural de tres con elementos concretos está bien.
- Cebo de interacción ("comenta SÍ", "etiqueta a 3 amigos", "doble toque si").
- Ráfagas entrecortadas y líneas de una palabra para dar dramatismo (la huella
  del humanizador), o un párrafo donde todas las líneas suenan planas.
- La firma de emojis de IA (🚀 ✨ 🔥 💯 🙌 🎯): se quita como conjunto. No dejes
  uno de esos emojis como único superviviente; si la voz del autor usa emojis,
  conserva los suyos, no los de la firma.
- Exceso de signos de exclamación y frases de vendedor ("¡No te lo pierdas!",
  "¡Descubre cómo!").

## Ejemplo

Ver `references/examples.md` para reescrituras completas de antes/después.

## Archivos

- `SKILL.md` - este archivo (limpiador de reescritura + entrada al modo auditoría)
- `references/scrub-rules.md` - patrones V3 por nivel, puntuación por densidad, límite de rayas, reglas de ritmo, inserciones prohibidas
- `references/examples.md` - reescrituras completas de antes/después para captions y slides
- `references/audit-checklist.md` - la lista de verificación previa a publicar, con umbrales
- `sub-skills/post-audit.md` - flujo de auditoría previa a publicar (solo detección, sin reescritura)
- `sub-skills/voice-profile.md` - crear/actualizar el Perfil de voz y marca del usuario (`--mode profile`)
- `sub-skills/illustration.md` - flujo opcional de imágenes con Pixfaro

## Modo perfil de voz (`--mode profile`)

`ig-humanizer --mode profile` crea o actualiza el Perfil de voz y marca del usuario en `../../references/voice-profile.md` a partir de 3-6 de sus posts reales de Instagram pegados en la conversación (portátil, sin token) o, si hay un token de lectura configurado, de su actividad obtenida. Una vez completo, todas las skills de redacción de este paquete escriben automáticamente con la voz del usuario. Ver `sub-skills/voice-profile.md`. Disparadores: "arma mi perfil de voz", "aprende mi voz".

## Skills relacionadas

- `ig-caption-writer` - genera captions que ya pasan el humanizador
- `ig-carousel-planner` - genera carruseles que ya pasan el humanizador
