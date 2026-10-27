# Reglas de voz para Instagram

Estas son las reglas de voz canónicas de todo el paquete. Todas las skills las
heredan. Las secciones locales de "Reglas estrictas" de cada skill solo agregan
excepciones propias del formato (largo de la descripción, cantidad de slides, tamaño
de hashtags) y remiten a este archivo.

## Idioma

- **Todo el contenido se escribe en español neutro**, con tuteo ("guarda este
  post", "escríbeme"), sin regionalismos ni modismos locales, salvo que el
  Perfil de voz del usuario (`voice-profile.md`) indique otra variante.
- **Respeta la ortografía del español**: tildes, signos de apertura (¿ ¡) y
  comillas. Omitir tildes no es un registro casual, se lee como descuido.
- **No traduzcas palabra por palabra desde el inglés.** Evita calcos como
  "aplicar" por "postularse", "librería" por "biblioteca", "remover" por
  "quitar", "en orden a" o "es por eso que" en exceso.
- **Los anglicismos propios de Instagram se aceptan** cuando son los que usa la
  gente: reel, post, carrusel, story/historia, feed, hashtag, link en la bio,
  hook (o gancho). No fuerces traducciones que nadie usa.

## Reglas estrictas

1. **Rayas (`—`) limitadas a aproximadamente 1 cada 100 palabras** (1-2 por
   descripción, como máximo 1 por slide de carrusel). En español la raya se usa en
   incisos y diálogos, así que no es un indicio de IA por sí sola; lo es la
   densidad. Reemplaza el exceso por coma, dos puntos, paréntesis o salto de
   línea, nunca por punto. Sin guiones (`-`) ni dobles guiones (`--`) entre
   oraciones.
2. **Usa `..` o un salto de línea** como pausa suave cuando estarías por poner
   una segunda raya. Se lee humano y coincide con cómo escribe la gente en
   Instagram.
3. **Escribe con mayúscula nombres de personas, empresas y productos** (Stripe,
   Canva, Figma). Una marca en minúscula se lee como descuido.
4. **Las oraciones pueden empezar en minúscula** en descripciones de tono casual; es
   propio del registro de Instagram. Los nombres propios siempre van con
   mayúscula. Si el Perfil de voz pide un registro formal, usa mayúscula inicial.
5. **Los números concretos le ganan a los adjetivos.** "ahorré 11 horas por
   semana" es mejor que "ahorré muchísimo tiempo". "4.200 USD en 30 días" es
   mejor que "gané buen dinero". Usa el punto como separador de miles y la coma
   decimal, salvo que el Perfil de voz indique otra convención.
6. **Una idea por descripción.** Una descripción que defiende tres puntos se lee como
   artículo de blog. Elige la que justifica el guardado.
7. **No vendas a la fuerza.** Instagram entierra las descripciones abiertamentes
   promocionales. Enseña o cuenta una historia y luego señala el siguiente paso
   una sola vez.

## Marcadores de vocabulario (se puntúan por densidad)

Cuéntalos por párrafo. Uno es español normal; dos es zona gris (márcalo en el
informe y deja las palabras); tres en un mismo párrafo se lee como IA y el
párrafo completo se reescribe (ver `ig-humanizar-texto` V3).

Marcadores típicos del texto generado por IA en español:
- **Verbos inflados:** potenciar, impulsar, optimizar, fomentar, aprovechar al
  máximo, desbloquear, catapultar, empoderar, elevar, maximizar, transformar,
  revolucionar, sumergirse, adentrarse, explorar (en sentido figurado),
  navegar (en sentido figurado), abordar
- **Adjetivos de relleno:** crucial, fundamental, esencial, clave, vital,
  significativo, integral, robusto, innovador, disruptivo, holístico, valioso,
  increíble, poderoso, sin igual
- **Adverbios y conectores:** fundamentalmente, esencialmente, en definitiva,
  en última instancia, cabe destacar, es importante destacar, sin lugar a dudas,
  además (al inicio de cada párrafo), asimismo, por otro lado
- **Sustantivos abstractos:** panorama, ecosistema, paradigma, ámbito, sinergia,
  viaje (en sentido figurado), camino, universo, mundo de (en "el mundo del
  marketing")

## Siempre prohibido (basta una aparición, sin importar la densidad)

Se eliminan en cuanto aparecen. Son puentes de revelación, paralelismos
negativos, frases muertas o sinceridad actuada, no simple vocabulario:
- "No se trata solo de X, se trata de Y" / "No es solo X, es Y"
- "En el mundo acelerado de hoy", "en la era digital", "en un mundo cada vez
  más competitivo"
- "un antes y un después", "cambia las reglas del juego", "llevarlo al
  siguiente nivel", "imprescindible", "sumérgete en", "descubre el poder de"
- "Link en la bio" como relleno (solo cuando hay un link real y una razón real)
- Anuncios de sinceridad al inicio o como giro: "seamos sinceros", "te voy a
  ser honesto", "¿honestamente?", "hablemos claro", "no te voy a mentir",
  "opinión impopular:" sobre una opinión que en realidad es popular. Di el hecho
  sin anunciarlo.
- Cierres de manual: "¡Espero que te sirva!", "¡Y tú qué opinas? ¡Déjamelo en
  los comentarios!", "Recuerda que…" como remate moralizante.

## Estilo nativo de Instagram

- **La primera línea es todo el trabajo.** Instagram oculta todo lo que sigue a
  los ~125 caracteres detrás de "más". Si la línea 1 no consigue el toque, el
  resto no se lee.
- **Los saltos de línea son puntuación.** El espacio en blanco entre líneas
  cortas marca el ritmo y hace que la descripción se pueda leer de un vistazo. Un
  bloque de texto se pasa de largo.
- **Los emojis son parte del registro, usados con moderación.** 0-3 por descripción,
  ubicados para cortar texto o marcar una lista, nunca espolvoreados. Una descripción
  con 12 emojis se lee como cuenta de spam o como IA.
- **Los hashtags son dimensionamiento, no volumen.** En 2026, 3-5 etiquetas bien
  dimensionadas le ganan a 30 al azar (ver `hashtag-strategy.md`). Ponlos al
  final de la descripción o en el primer comentario, nunca a mitad de una oración.
  Para audiencias hispanohablantes prioriza hashtags en español.

## Largo

- **Límite de la descripción: 2.200 caracteres.** Solo los primeros ~125 se ven antes
  de "más", así que el gancho va adelante. El español ocupa alrededor de un 20%
  más que el inglés: recorta palabras antes que perder el gancho. La mayoría de
  las buenos descripciones quedan entre 150 y 1.500 caracteres; uno largo está bien
  cuando enseña o cuenta una historia que vale la pena.
- **La descripción de un carrusel puede ser corta** porque las slides llevan el
  contenido. Un post de una sola imagen depende más de la descripción.
- **Descripción de reel: breve.** El video es el gancho; la descripción agrega contexto
  y la razón para guardar o compartir en una o dos líneas.

## Estructura

- **Gancho adelante**, en la primera línea (antes del corte). Plantea el
  beneficio, la tensión o el número desde el principio.
- **Cierra con un aterrizaje, no con una pregunta muerta.** "¿Qué opinas?" está
  muerta. Una pregunta concreta, una invitación a guardar que nombra la razón
  ("guárdalo para tu próximo lanzamiento") o una frase de cierre filosa le ganan.
- **Carruseles:** la slide 1 es el gancho; la última es la recompensa más el
  pedido de guardar o seguir. Ver `hook-formulas.md` y el planificador de
  carruseles.

## Antipatrones

- Descripción que repite lo obvio ("El marketing es muy importante hoy en día").
- Cebo genérico de interacción ("doble toque si estás de acuerdo", "comenta SÍ").
- Aperturas gastadas: "Hablemos de..", "Te cuento algo..", "POV:" sobre algo que
  no es un punto de vista.
- Tríadas apiladas o huecas ("más rápido, más barato, mejor"); una enumeración
  natural de tres elementos concretos está bien.
- Una primera línea que necesita la línea 2 para entenderse (el corte se la come).
- Más de 20 hashtags amontonados al inicio de la descripción.
- Líneas en MAYÚSCULAS para dar intensidad. La intensidad va en la elección de
  palabras.
- Exceso de signos de exclamación (¡¡¡!!!) y de diminutivos afectados.

## Nota sobre el algoritmo

En 2026 el ranking de Instagram se apoya en **envíos por alcance** (compartidos
a amigos y a la propia historia) y en **guardados** como las señales más fuertes
de que un contenido vale la pena difundirse, por encima de los "me gusta". Antes
de publicar, verifica: ¿esto le da a quien lo ve una razón para enviárselo a un
amigo concreto o para guardarlo para después? Si solo consigue un "me gusta"
pasivo, afínalo.
