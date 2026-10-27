# Heurísticas de publicación en Instagram 2026

Sintetizadas a partir de las declaraciones públicas de Instagram sobre ranking
(publicaciones de Adam Mosseri para creadores), los explicadores del algoritmo
de 2023-2026 y datos observados de creadores. Los números marcados como
"reportado" son mediciones de la comunidad, no confirmaciones oficiales.
Instagram ordena cada superficie (Feed, Reels, Explorar, Historias) con su
propio modelo, pero las señales de abajo se generalizan.

## Contenido

- Peso de las señales (impacto relativo en el alcance)
- Los primeros 30-60 minutos
- Lo que reduce el alcance (evitar)
- Lo que amplifica el alcance
- Límites de formato y archivos (vía la API de publicación)
- Carruseles
- Reels
- Historias
- Horarios
- Guardados y envíos son las palancas subestimadas
- Lista de verificación antes de publicar

## Peso de las señales (impacto relativo en el alcance)

Instagram puntúa la interacción prevista, y los tipos de interacción no valen
lo mismo. Pesos relativos reportados a partir de pruebas de creadores y
declaraciones de la plataforma:

| Señal | Peso relativo | Nota |
|---|---|---|
| **Envío / compartido** (a un amigo por DM o republicado en historia) | el más alto | "envíos por alcance" es la métrica en la que más se apoya el algoritmo en 2026 |
| **Guardado** | alto | la señal de "voy a volver a esto"; impulsa tutoriales, listas y marcos de trabajo |
| **Comentario** (sobre todo si el autor responde) | alto | una conversación real es una señal fuerte de calidad |
| **Tiempo de reproducción / finalización / repetición de reels** | alto (Reels) | en video, la retención y la repetición deciden el impulso |
| **Visita al perfil y luego seguimiento** | alto | la señal de crecimiento; el contenido con recompensa la consigue |
| **Me gusta** | bajo | aprobación barata, poco alcance |
| **Negativas: "no me interesa", dejar de seguir, ocultar, denunciar** | penalización fuerte | una denuncia pesa más que muchos "me gusta" |

Conclusión: optimiza para **envíos, guardados y comentarios**, no para "me
gusta". La pregunta más útil antes de publicar: ¿quien lo vea se lo enviaría a
un amigo concreto o lo guardaría para usarlo después?

## Los primeros 30-60 minutos

- La ventana inicial marca la trayectoria. Los guardados, envíos y comentarios
  tempranos le indican al ranking que amplíe la distribución a no seguidores en
  Explorar y en el feed de Reels.
- **Responde rápido los primeros comentarios.** Las respuestas del autor atraen
  más comentarios y señalan una conversación activa.
- Un reel que sostiene la retención durante los primeros 3 segundos en la
  prueba inicial consigue un impulso más amplio.

## Lo que reduce el alcance (evitar)

- **El cebo de interacción** ("comenta SÍ", "etiqueta a 3 amigos", "doble toque
  si") se penaliza explícitamente.
- **Videos republicados o reciclados con la marca de agua de otra app** (un logo
  visible de otra plataforma) se suprimen en Reels.
- **Descripciones hechos solo de hashtags** (20-30 etiquetas amontonadas arriba) se
  leen como spam en 2026 y no ayudan al alcance. La recomendación actual son 3-5
  etiquetas dimensionadas.
- **Relaciones de aspecto fuera del rango 4:5 a 1,91:1** se recortan, lo que
  perjudica un carrusel o una imagen del feed.
- **Una tasa alta de ocultar/dejar de seguir/denunciar** hunde la distribución
  rápidamente.
- **Mezclar formatos en un carrusel** la API lo rechaza directamente.

## Lo que amplifica el alcance

- **Los envíos son la palanca.** Un post pensado para enviárselo a un amigo (una
  verdad identificable, una lista útil, un "tienes que ver esto") llega más lejos
  que uno que busca "me gusta".
- **Los guardados se acumulan.** Los formatos que invitan a guardar (listas,
  marcos, tutoriales, antes/después) siguen ganando alcance durante días a
  medida que Explorar los muestra.
- **Los reels con buena retención** son el formato que más se impulsa a no
  seguidores en 2026. El audio original y el texto en pantalla ayudan.
- **Los carruseles tienen una segunda oportunidad:** quien no deslizó puede ver
  la slide 2 cuando se vuelve a mostrar, así que Instagram a veces los vuelve a
  presentar y tienen una vida más larga.
- **Responder tus propios comentarios y DMs** en la primera hora mantiene viva
  la señal de conversación.

## Límites de formato y archivos (vía la API de publicación)

| Elemento | Límite |
|---|---|
| Descripción | 2.200 caracteres (los primeros ~125 visibles antes de "más") |
| Hashtags | 30 como máximo por post (pero en 2026 la práctica son 3-5 dimensionados) |
| Elementos de carrusel | 2-10 (API; la app nativa permite 20) |
| Formatos de imagen | JPEG, PNG, WebP (WebP se convierte a JPEG) |
| Tamaño máximo de imagen | 8 MB |
| Duración de reel | hasta 3 min (180 s) vía API; 5-90 s son aptos para la pestaña Reels |
| Tamaño máximo de reel/video | 300 MB |
| Video en carrusel | hasta 60 s por clip |
| Formatos mezclados en carrusel | no permitido (todo imágenes o todo video) |
| Relación de aspecto | de 4:5 (vertical) a 1,91:1 (horizontal); el 4:5 vertical ocupa todo el feed |
| Límite de frecuencia | ~50 posts / 24 h (algunas cuentas reportan 25) |

- **Todo post requiere contenido multimedia.** Instagram rechaza los posts solo
  de texto. Las skills de redacción producen la descripción; el usuario aporta la
  imagen o el video.
- Una imagen se publica como foto; 2-10 imágenes, como carrusel; un video, como
  reel por defecto (o como historia con `videoType: "STORIES"`).

## Carruseles

- **La slide 1 es todo el embudo.** Tiene que prometer una recompensa y abrir un
  bucle, o nadie desliza. Todo lo demás solo importa si la slide 1 consigue el
  deslizamiento.
- **Valor adelante.** El deslizamiento cae con la profundidad, así que el mejor
  elemento va en la slide 2 o 3, no guardado para la 10.
- **Largo óptimo: 6-10 slides** para un carrusel educativo o de lista. Cada
  slide plantea una sola idea y se entiende sola.
- **La última slide consigue el guardado y el seguimiento.** Cierra con un
  resumen en una slide (lo que se guarda) y un único pedido claro.
- **Diseña para el formato 4:5.** El vertical ocupa más pantalla y retiene la
  atención.

## Reels

- **Los primeros 1-3 segundos deciden el alcance.** Abre con una ruptura de
  patrón, un gancho en texto en pantalla y el punto. Nada de "hola a todos,
  bienvenidos de nuevo".
- **El objetivo es retención y repetición.** Un final que enlaza con el inicio
  (el último cuadro fluye hacia el primero) aumenta las repeticiones.
- **El texto en pantalla** permite captar el gancho a quien mira sin sonido y
  mejora la finalización.
- **El audio original o en tendencia** ayuda, pero el gancho y la retención
  importan más.
- Sin marca de agua visible de otra app de video.

## Historias

- **Las historias no impulsan el alcance** hacia no seguidores; profundizan la
  relación con los seguidores actuales y te mantienen presente.
- **Republicar tu post del feed en tu historia** es una señal equivalente a un
  envío y lleva el original a seguidores que no lo vieron.
- Los stickers interactivos (encuesta, pregunta, quiz) consiguen los toques que
  te mantienen al frente de la bandeja de historias.

## Horarios

| Audiencia | Mejores franjas (hora local) |
|---|---|
| Creadores / consumidores de EE. UU. | días de semana 11-13 h y 19-21 h, más el domingo por la tarde-noche |
| B2B / fundadores | martes a jueves a media mañana y al mediodía |
| Audiencias hispanohablantes u otras | no hay datos publicados confiables en las fuentes de este paquete: publica cuando tu audiencia concreta está conectada (revisa tus estadísticas de Instagram) |

- La constancia le gana a la frecuencia pura. 3-5 posts de calidad por semana
  con un ritmo estable rinden más que un volcado diario de relleno.
- Los reels se pueden publicar más seguido que los carruseles sin saturar,
  porque cada uno llega a una audiencia nueva de no seguidores.

## Guardados y envíos son las palancas subestimadas

- Un **guardado** significa que quien lo vio piensa volver: premia listas,
  marcos de trabajo, tutoriales y contenido de antes/después. Diseña cebo de
  guardado a propósito (IG5, IG8, IG10, IG1, IG6).
- Un **envío** significa que quien lo vio pensó en una persona concreta: premia
  verdades identificables, derriba mitos y posturas a contracorriente (IG2,
  IG7, IG3, IG9).
- Los dos amplían el alcance mucho más que un "me gusta". Las etiquetas de
  objetivo de las fórmulas de gancho asignan cada fórmula a guardados,
  compartidos, comentarios o seguidores.

## Lista de verificación antes de publicar

- [ ] Los primeros 125 caracteres de la descripción frenan el scroll por sí solos.
- [ ] Rayas (`—`) en una cada 100 palabras o menos (nunca reemplazar una por punto); sin guiones entre oraciones ni dobles guiones (`--`).
- [ ] Sin acumulación de vocabulario de IA (3 o más marcadores en un párrafo: potenciar, fundamental, cabe destacar, etc.).
- [ ] Al menos un número de precisión poco redonda con un referente nombrado, cuando la afirmación lo permite.
- [ ] Ortografía revisada: tildes, signos de apertura (¿ ¡).
- [ ] 3-5 hashtags dimensionados (no 30), al final o en el primer comentario.
- [ ] 0-3 emojis, ubicados con intención, ninguno espolvoreado.
- [ ] La slide 1 del carrusel promete y abre un bucle; la última cumple y pide.
- [ ] Contenido multimedia aportado y dentro de los límites (JPEG/PNG/WebP, sin mezclar formatos, 2-10 slides).
- [ ] El cierre es un aterrizaje o un pedido concreto de guardar/enviar, no "¿qué opinas?".
- [ ] Un objetivo principal claro (guardados / compartidos / comentarios / seguidores), no todos a la vez.
