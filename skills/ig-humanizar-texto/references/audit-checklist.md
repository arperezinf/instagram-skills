# Lista de auditoría previa a publicar (Instagram)

Los umbrales que aplica la pasada `--mode audit`. Replica la lista de
`references/algorithm-heuristics.md` de la raíz, con las distinciones de
bloqueantes del humanizador. V3 (2026-09): los indicios de IA se puntúan por
densidad por párrafo; las rayas se limitan a aproximadamente 1 cada 100
palabras, no se prohíben; el ritmo forzado es un indicio.

## Bloqueantes (reprobado automático)

- [ ] Rayas (`—`) en 1 cada 100 palabras o menos (1-2 por caption; como máximo
      una por slide de carrusel). Una raya sola nunca es bloqueante. Sin guiones
      entre oraciones ni dobles guiones (`--`).
- [ ] Los primeros 125 caracteres se sostienen solos como gancho (el corte de
      "más" oculta el resto).
- [ ] Caption dentro de los 2.200 caracteres.
- [ ] 3-5 hashtags dimensionados, no 20-30, nunca a mitad de oración.
- [ ] Sin cebo de interacción ("comenta SÍ", "etiqueta a 3 amigos", "doble
      toque si").
- [ ] Sin apertura del tipo "En el mundo acelerado de hoy" o equivalente; sin
      apertura con puente de revelación ("Te cuento algo..", "Hablemos de..",
      "Deja de X, empieza a Y"); sin apertura con anuncio de sinceridad
      ("hablemos claro", "no te voy a mentir", "POV:" sobre algo que no es un
      punto de vista).
- [ ] Sin cierre muerto "¿Qué opinas?" / "¿Opiniones?" / "Léelo de nuevo." (una
      invitación a guardar o enviar con una razón está bien y se busca).
- [ ] Ningún párrafo con 3 o más marcadores de vocabulario o gramática (un
      marcador por párrafo está bien); sin paralelismo negativo "No es solo X,
      es Y"; sin puente de revelación "¿El resultado?".
- [ ] Ortografía: signos de apertura (¿ ¡) presentes y tildes correctas, salvo
      omisión deliberada indicada en el Perfil de voz.
- [ ] Carrusel: todo imágenes o todo video (sin mezclar formatos), 2-10 slides.
- [ ] Existe un plan de contenido multimedia (Instagram rechaza los posts solo
      de texto).

## Advertencias (señalar con corrección)

- [ ] El set de hashtags está dimensionado (2-3 de nicho, 1-2 medios, 0-1
      amplio), no son todos amplios; prioridad al español si la audiencia es
      hispanohablante.
- [ ] 0-3 emojis, ubicados con intención, ninguno espolvoreado; sin la serie
      característica de cohete/destellos/fuego.
- [ ] Ningún párrafo suena plano como máquina (4 o más oraciones del mismo
      largo, sin cláusula que trabaje). Señala solo ese párrafo; nunca sugieras
      agregar variación como táctica. La diagramación de una idea por línea está
      bien.
- [ ] Sin ráfagas entrecortadas ("Corto. Directo. Listo.", "Sin X. Sin Y. Solo
      Z."), sin líneas de una palabra para dar dramatismo, como máximo 2
      fragmentos sueltos en el caption, sin vaivén largo/corto/largo/corto.
- [ ] Al menos un número de precisión poco redonda CON un referente nombrado
      donde la afirmación lo permita (un número pelado no cumple).
- [ ] Al menos una entidad con nombre.
- [ ] Como máximo una enumeración natural de tres; sin tríadas apiladas o
      perfectamente paralelas, sin tríadas huecas sin elementos concretos, nunca
      3 o más en un caption.
- [ ] Sin acumulación de atenuantes ("quizás", "pareciera que", "puede que me
      equivoque, pero") ni confesiones enmarcadas ("hablemos claro, esto dolió:
      ..."). Un hecho fechado dicho sin rodeos está bien.
- [ ] Sin calcos del inglés (mayúscula en cada palabra de un título, "aplicar a
      un trabajo", "hacer sentido", pasiva con "ser" innecesaria).
- [ ] Solo al auditar una reescritura del humanizador con el original a mano, no
      un borrador nuevo: no hubo sobrelimpieza, es decir, sobrevivieron el tono
      del autor, sus reacciones, su registro en minúscula, una raya, una tríada
      natural y sus emojis intencionales.
- [ ] La slide 1 del carrusel promete y abre un bucle, no es un título pelado.
- [ ] El punto más fuerte del carrusel está adelante (slide 2-3), no enterrado al
      final.
- [ ] Un objetivo principal claro (guardados / compartidos / comentarios /
      seguidores).
- [ ] Una llamada a la acción, no tres; nombra una razón.

## Referencia rápida de umbrales

| Métrica | Límite |
|---|---|
| Caption | 2.200 caracteres (gancho en los primeros ~125) |
| Hashtags | 3-5 dimensionados (30 es el tope técnico pero es spam) |
| Emojis por caption | 0-3 |
| Rayas | aproximadamente 1 cada 100 palabras (1-2 por caption; 1 por slide) |
| Marcadores de vocabulario / gramática por párrafo | 0-2 |
| Fragmentos sueltos | 2 por caption |
| Slides de carrusel | 2-10 |
| Duración de reel | hasta 3 min; 5-90 s para la pestaña Reels |
| Relación de aspecto | de 4:5 a 1,91:1 |

## Puntuación

- Cualquier bloqueante -> **REPROBADO**, devuelve las correcciones y ofrece la
  reescritura automática con `ig-humanizar-texto`.
- Sin bloqueantes y con advertencias -> **APROBADO con advertencias**, lista cada
  una con su corrección.
- Limpio -> **APROBADO**, agrega la nota de horarios, la verificación de la
  superficie y el recordatorio de contenido multimedia.
- Informa la densidad de indicios por párrafo (marcadores, rayas cada 100
  palabras, fragmentos, tríadas). No estimes un puntaje de detector: en textos
  del largo de un caption son ruido y esta skill no promete superarlos.
