# Auditoría de posts de Instagram

Pasa cualquier descripción (y el texto de las slides de un carrusel) por la lista de
verificación de ranking de Instagram 2026. Detecta indicios de IA, violaciones
de formato (gancho de 125 caracteres, largo de la descripción, dimensionamiento de
hashtags, emojis), lo que reduce el alcance (cebo de interacción, formatos
mezclados) y debilidades estructurales antes de publicar. Es el flujo de
`ig-humanizar-texto --mode audit`: solo detección, sin reescritura. El informe se
entrega en español.

## Cuándo usarla

- Antes de publicar una descripción o carrusel escrito a mano o redactado con IA
- Cuando `ig-redactar-descripcion` o `ig-planificar-carrusel` terminan un borrador (se invoca automáticamente)
- Cuando un post reciente rindió menos de lo esperado y el usuario quiere un análisis

## Entrada

- Una descripción y, para un carrusel, el texto de las slides
- Opcional: audiencia objetivo, horario programado, la superficie (imagen / carrusel / reel)

## Salida

- Encabezado **Aprobado / Reprobado**
- **Bloqueantes** (hay que corregirlos antes de publicar): densidad de rayas por
  encima del límite, párrafos con 3 o más marcadores de IA, puentes de
  revelación, un anuncio de sinceridad como apertura, cebo de interacción, un
  gancho que se pasa del corte, muros de hashtags, signos de apertura ausentes
- **Advertencias** (riesgosas para publicar): ráfagas entrecortadas,
  marcadores de sinceridad o atenuantes a mitad de la descripción (como apertura son
  bloqueantes), falta de números con referente, llamada a la acción genérica,
  calcos del inglés
- **Correcciones sugeridas** para cada problema
- **Densidad de indicios por párrafo** (marcadores, rayas cada 100 palabras,
  fragmentos, tríadas). Sin puntaje de detector: en textos del largo de un
  descripción son ruido y la skill no promete superarlos
- **Recomendación de horario** según la audiencia

## Verificaciones

### Bloqueantes (reprobado automático)

1. Densidad de rayas por encima de aproximadamente 1 cada 100 palabras (1-2 por
   descripción; más de una en una slide de carrusel); guion entre oraciones; doble
   guion. Una raya sola no es bloqueante.
2. El gancho necesita la segunda línea para entenderse (los primeros 125
   caracteres no se sostienen solos).
3. Descripción de más de 2.200 caracteres.
4. 20-30 hashtags, o hashtags a mitad de oración.
5. Cebo de interacción ("comenta SÍ", "etiqueta a 3 amigos", "doble toque si
   estás de acuerdo").
6. Abre con "En el mundo acelerado de hoy" o similar, un puente de revelación
   ("Te cuento algo..", "Hablemos de..", "Deja de X, empieza a Y") o un anuncio
   de sinceridad ("hablemos claro", "no te voy a mentir", "POV:" sobre algo que
   no es un punto de vista).
7. Termina con "¿Qué opinas?", "¿Opiniones?" o "Léelo de nuevo." (una invitación
   a guardar o enviar con una razón está bien).
8. Cualquier párrafo con 3 o más marcadores de vocabulario o gramática, o
   cualquier paralelismo negativo / puente de revelación "¿El resultado?" (ver
   `../references/scrub-rules.md`).
9. Preguntas o exclamaciones sin signo de apertura (¿ ¡), salvo omisión
   deliberada indicada en el Perfil de voz.
10. El carrusel mezcla imágenes y video, o tiene más de 10 slides.
11. No hay plan de contenido multimedia (Instagram rechaza los posts solo de texto).

### Advertencias (señalar con una corrección sugerida)

12. Más de 5 hashtags, o un set de solo etiquetas amplias en las que una cuenta
    chica no puede posicionarse.
13. 4 o más emojis, emojis espolvoreados en cada línea, o la serie característica
    de cohete/destellos/fuego.
14. Un párrafo que suena plano como máquina (4 o más oraciones del mismo largo,
    sin cláusula que trabaje). Señala solo ese párrafo; nunca sugieras agregar
    variación como táctica. La diagramación de una idea por línea está bien.
14a. Ráfagas entrecortadas ("Corto. Directo. Listo.", "Sin X. Sin Y. Solo Z."),
    líneas de una palabra para dar dramatismo, más de 2 fragmentos sueltos o un
    vaivén largo/corto/largo/corto.
15. Ningún número de precisión poco redonda con referente nombrado donde la
    afirmación lo permitiría (un número pelado no cumple).
16. Ninguna entidad con nombre (persona, marca, herramienta).
17. Regla de tres apilada o perfectamente paralela, una tríada hueca sin
    elementos concretos, o 3 o más tríadas en la descripción (una tríada natural
    pasa).
17a. Acumulación de atenuantes ("quizás", "pareciera que") o un marcador de
    sinceridad / confesión enmarcada a mitad de la descripción ("hablemos claro, esto
    dolió: ..."); el mismo marcador como apertura es el bloqueante 6. Un hecho
    fechado dicho sin rodeos está bien.
17b. Sobrelimpieza (solo al auditar una reescritura del humanizador con el
    original a mano para comparar; un borrador nuevo que nunca tuvo raya ni
    tríada no está sobrelimpiado): tono uniformemente plano, todas las rayas y
    tríadas quitadas de una descripción larga, desaparecieron los emojis o el
    registro en minúscula del autor, sin reacción ni opinión en ninguna parte.
17c. Calcos del inglés: mayúscula en cada palabra de un título, falsos amigos
    ("aplicar a", "eventualmente", "hacer sentido"), pasiva con "ser" innecesaria.
18. La slide 1 del carrusel es un título pelado, no una promesa + bucle abierto.
19. El punto más fuerte del carrusel está enterrado en la última slide del cuerpo.
20. No hay un objetivo principal claro: el borrador persigue guardados,
    compartidos, comentarios y seguidores al mismo tiempo. Elige uno (ver
    `../../../references/hook-formulas.md`, "Reparto por objetivo de
    interacción").
21. La llamada a la acción es genérica o hay tres compitiendo.

### Información (notas neutrales)

22. Franja de publicación sugerida según la audiencia (si no hay datos de esa
    audiencia, recomienda revisar sus estadísticas de Instagram en lugar de
    inventar un horario).
23. Recomendación de superficie (imagen única, carrusel o reel) según el material.
24. Oportunidad de guardado/envío: si el borrador es una lista, un marco o un
    tutorial, indica que debe estructurarse para maximizar guardados; si es una
    recompensa a contracorriente o de mito, para maximizar envíos.

## Pasos

1. Detecta la superficie: imagen única, carrusel o reel.
2. Mide la descripción: cantidad de caracteres, dónde corta en los primeros 125,
   cantidad y tamaño de hashtags, cantidad de emojis, rayas cada 100 palabras.
3. Ejecuta las verificaciones bloqueantes. Si alguna falla, devuelve
   **REPROBADO** con correcciones concretas; opcionalmente ofrece pasarlo a
   `ig-humanizar-texto` para una reescritura automática.
4. Si no hay bloqueantes, ejecuta las advertencias.
5. Informa la densidad de indicios por párrafo. No estimes un puntaje de detector.
6. Devuelve el informe estructurado con una nota de horario y un recordatorio
   de contenido multimedia.

## Relacionadas

- `ig-humanizar-texto` - reescritura proporcional si la auditoría falla
- `ig-redactar-descripcion` / `ig-planificar-carrusel` - regenerar con una fórmula probada
