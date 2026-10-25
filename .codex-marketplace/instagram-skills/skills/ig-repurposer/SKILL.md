---
name: ig-repurposer
description: "Adapta contenido existente a un post nativo de Instagram en español. Toma un post de LinkedIn, un blog, un guion de YouTube o un tuit o hilo de X y lo reconstruye: una pieza larga pasa a carrusel o caption, con nuevo gancho antes del corte de 125 caracteres, sin restos de otra plataforma, traducido y adaptado si la fuente está en otro idioma, y publicado vía Publora al aprobarse. No para escribir desde cero (usa ig-caption-writer o ig-carousel-planner) ni auditar (ig-humanizer --mode audit)."
---

# Adaptador de contenido para Instagram

Convierte algo que ya hiciste en un post que se lea como nacido en Instagram.
Adaptar no es copiar y pegar. Un post que arrasó en LinkedIn o un hilo que voló
en X mueren en Instagram si los pegas: gancho equivocado, contenedor
equivocado, ritmo equivocado, sin contenido multimedia y con restos ("link en
la bio", @usuarios, muros de hashtags) que delatan otra plataforma.

Esta skill transforma, no genera. Lee tu fuente, conserva la idea y reconstruye
la entrega para Instagram. El resultado se escribe en español neutro, salvo que
el Perfil de voz indique otra variante.

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

- "Convierte este post de LinkedIn en un carrusel / caption de Instagram"
- "Adapta mi artículo del blog / newsletter / guion de YouTube para Instagram"
- "Este hilo funcionó en X, adáptalo a Instagram"
- "Tengo una idea en otro formato, hazla nativa de acá"
- "Tengo este contenido en inglés, adáptalo en español para Instagram"

No para un borrador desde cero (usa `ig-caption-writer` para un caption,
`ig-carousel-planner` para un carrusel slide por slide) ni para revisar un
borrador que ya es de Instagram (usa `ig-humanizer --mode audit`).

## Cómo funciona

**Primero el Perfil de voz (en todos los borradores).** Si `../../references/voice-profile.md` tiene `filled: yes`, cárgalo y respeta en todo el texto la huella de voz, las reglas estrictas, la variante de español y el estilo de llamada a la acción y de links del usuario. Si no está completo, menciona una vez que `ig-humanizer --mode profile` puede aprender su voz a partir de algunos posts y sigue con las reglas de voz genéricas.

**Nunca inventes los datos concretos.** Las reglas de abajo piden un número concreto, una fecha y una entidad con nombre, porque eso es lo que separa un post real de uno generado. Tómalos de lo que el usuario dijo en esta conversación o de la fuente. **No inventes una cifra, una fecha, el nombre de un cliente ni un resultado, y no conviertas una afirmación vaga en un número de aspecto creíble.** Si el usuario no tiene nada concreto para un tramo, pregúntale una vez; si sigue sin tenerlo, quita la afirmación en lugar de adornarla. Un número inventado y publicado obliga a retractarse; uno ausente solo hace un post más débil.

1. **Toma la fuente.** Cualquier formato: un post, un párrafo, un guion, un
   caption, una transcripción, una lista, un link para leer. Pide la fuente, el
   contenido multimedia que tiene el usuario (Instagram necesita imagen o video)
   y el objetivo (guardados / compartidos / comentarios / seguidores) si no se
   indicó.
2. **Extrae la columna.** Quita el envoltorio de la plataforma de origen y saca
   la única afirmación, historia o número que vale la pena conservar. La mayoría
   de las adaptaciones fallan porque conservan las palabras en lugar del punto.
3. **Si la fuente está en otro idioma, adapta, no traduzcas literal.** Conserva
   la idea y los datos; reescribe con construcciones naturales del español,
   cambia ejemplos o referencias que no se entiendan en el mercado del usuario
   (avísale cuando lo hagas) y convierte formatos de cifras y fechas a la
   convención del Perfil de voz.
4. **Elige el contenedor.** Una afirmación o un número -> un caption. Una
   enseñanza, una lista o un proceso -> carrusel, una idea por slide (pásale la
   estructura a `ig-carousel-planner`, de la slide de gancho a la slide final).
   Un video largo -> un carrusel que entregue la recompensa, no un resumen.
5. **Nuevo gancho para el corte.** Instagram oculta todo lo que sigue a los ~125
   caracteres detrás de "más". La primera línea (o la slide de gancho) tiene que
   dar todo el golpe por sí sola. El gancho de la fuente casi nunca sobrevive;
   escribe una nueva primera línea con una fórmula de Instagram 2026 (ver
   `../../references/hook-formulas.md`), elegida según el objetivo.
6. **Reajusta el formato.** Cuerpo del caption fácil de leer, líneas cortas,
   espacio en blanco entre tramos. Carrusel: una idea por slide, sin bloques.
   Corta el tejido conectivo de la fuente; Instagram premia la recompensa
   adelantada.
7. **Quita los restos de otra plataforma.** Elimina el "link en la bio" que
   venía de otra plataforma, "suscríbete y activa la campanita", "sigue leyendo
   abajo", @usuarios de X que solo existen ahí y cualquier carraspeo del tipo
   "como escribí en LinkedIn". Un post adaptado no debería confesar que lo es.
8. **Recordatorio de contenido multimedia.** Instagram rechaza los posts solo de
   texto. Confirma la imagen, el video o el set de slides que adjuntará el
   usuario. Un caption sin contenido no se puede publicar.
9. **Hashtags al final.** Pásale el tema a `ig-hashtag-strategist` o aplica tú
   mismo un set dimensionado de 3-5 (ver `../../references/hashtag-strategy.md`),
   priorizando hashtags en español. Ponlos en un solo bloque al FINAL del
   caption o en el primer comentario, nunca como muro en medio del texto.
10. **Pasada del humanizador.** Aplica `ig-humanizer` V3 al resultado:
    vocabulario de IA por densidad de párrafo, rayas por encima del límite
    (alrededor de una cada 100 palabras, nunca reemplazadas por punto), tríadas
    apiladas, aperturas genéricas, puentes de revelación y calcos del inglés.
    Corrige solo un párrafo que suene plano como máquina; nunca fabriques
    variación. Conserva los números reales y las entidades con nombre de la
    fuente.
11. **Tarjeta de aprobación.** Muestra: el mapeo fuente -> Instagram (qué se
    convirtió en qué), el contenedor (caption o carrusel de N slides), la
    fórmula usada, el gancho (indica si supera los 125 caracteres), el set de
    hashtags, el contenido que debe adjuntar el usuario y el objetivo principal.
12. **Al aprobarse.** Publica con `lib.publish(kind="post",
    draft_text=<caption aprobado>, target_url="https://www.instagram.com/",
    media=[<rutas de archivos locales>], platforms=[<INSTAGRAM_PLATFORM_ID>],
    scheduled_time=<iso_o_None>)`. Para un reel pasa `kind="reel"`. El
    envoltorio ejecuta el flujo de Publora: borrador, subida y programación. Sin
    contenido o sin clave de Publora devuelve un bloque para copiar y pegar y un
    recordatorio de adjuntar el contenido.

## Reglas de ajuste nativo (fuente -> Instagram)

- **Post de LinkedIn -> Instagram:** un post largo pasa a carrusel (una idea por
  slide) o, si es una sola afirmación filosa, a un caption. LinkedIn tolera el
  precalentamiento; Instagram no. El gancho de LinkedIn suele ser demasiado
  largo; reescríbelo para el corte de 125 caracteres.
- **Blog / newsletter -> carrusel:** convierte la estructura en slides, una idea
  por slide, la slide de gancho primero y la final al último. No pegues toda la
  pieza en un caption.
- **Guion de YouTube -> carrusel con la recompensa:** abre con la recompensa del
  video, no con su introducción. Arma el carrusel en torno a "esto es lo que
  encontré", no un resumen escena por escena.
- **Tuit / hilo -> caption o carrusel:** un tuit pasa a caption; un hilo pasa a
  carrusel, un tuit por slide con su propia microidea. Quita los @usuarios de X
  y la numeración del hilo.

## Reglas estrictas

Reglas de voz globales: ver la sección de reglas de voz del `SKILL.md` raíz.
Reglas adicionales propias de esta skill:

- Conserva intactos **la afirmación y los datos** de la fuente. Adaptar cambia
  la entrega, nunca el significado ni los números.
- La nueva primera línea (o slide de gancho) tiene que frenar el scroll por sí
  sola antes del corte de 125 caracteres. Si necesita la segunda línea,
  reescríbela.
- Nunca pegues la fuente textual para después recortarla. Reconstruye el gancho
  y el ritmo a partir de la columna.
- Un número concreto donde la fuente lo ofrezca. Consérvalo.
- 3-5 hashtags dimensionados en un solo bloque al final, nunca 30 y nunca a
  mitad del caption.
- El contenido multimedia es obligatorio. Nunca presentes un caption adaptado
  como listo para publicar sin recordarle al usuario que adjunte la imagen, el
  video o las slides.
- No vendas a la fuerza el producto del usuario. Como máximo, una mención natural.

## Antipatrones (la skill se niega)

- Copiar y pegar la fuente con ediciones leves (eso no es adaptar).
- Traducción literal palabra por palabra desde otro idioma.
- Conservar los restos de la plataforma de origen ("link en la bio",
  "suscríbete", @usuarios de X, numeración del hilo).
- Un gancho que solo se entiende después del corte de 125 caracteres.
- Un muro de hashtags a mitad del caption en lugar de un bloque al final.
- Presentar un caption sin contenido multimedia como listo para publicar.
- Primera línea en MAYÚSCULAS para dar intensidad. La intensidad va en la
  elección de palabras.
- Rayas por encima del límite (más de una cada 100 palabras aproximadamente), o
  una raya reemplazada por punto.
- Puentes de revelación "¿El resultado?" / "Te cuento algo.." y ráfagas
  entrecortadas agregadas durante la reescritura.
- Listas de tres sin datos concretos.
- "potenciar", "fundamental", "un antes y un después", "llevarlo al siguiente
  nivel", "sumérgete en".
- Carraspeos meta ("Esto lo publiqué originalmente en...").

## Recursos

- `../../references/hook-formulas.md` - los esqueletos de las 10 fórmulas de Instagram para el nuevo gancho
- `../../references/algorithm-heuristics.md` - reglas de ranking de Instagram 2026 (corte, horarios, señales)
- `../../references/hashtag-strategy.md` - la receta de 3-5 hashtags dimensionados
- `../../references/media-workflow.md` - el flujo de borrador, subida y programación

## Skills relacionadas

- `ig-caption-writer` - escribe un caption nuevo desde cero
- `ig-carousel-planner` - estructura un carrusel slide por slide (el adaptador le pasa las piezas largas)
- `ig-hashtag-strategist` - arma el set de hashtags dimensionado
- `ig-humanizer` - limpia indicios de IA, más `--mode audit` para revisar el resultado
