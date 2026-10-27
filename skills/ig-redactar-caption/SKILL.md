---
name: ig-redactar-caption
description: "Redacta en español un caption de Instagram con el gancho en los primeros 125 caracteres, cuerpo fácil de leer y una sola llamada a la acción, con una fórmula de gancho 2026 elegida por objetivo (guardados, compartidos, comentarios, seguidores). Pasa el humanizador y, al aprobarse, publica con tu imagen o video vía Publora. Para una imagen o un reel. No para carruseles slide por slide (usa ig-planificar-carrusel) ni para auditar un borrador (usa ig-humanizar-texto --mode audit)."
---

# Redactor de captions para Instagram

Escribe un caption que consiga el toque y el guardado. Instagram oculta todo lo
que sigue a los ~125 caracteres detrás de "más", así que el gancho hace todo el
trabajo en la primera línea. Esta skill pone ese gancho adelante, mantiene el
cuerpo fácil de leer y cierra con una única llamada a la acción clara.

Todo el texto se escribe en español neutro, según `../../references/voice-rules.md`,
salvo que el Perfil de voz indique otra variante.

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

- El usuario dice "escríbeme un caption de Instagram sobre X"
- El usuario tiene una imagen o un reel y necesita el caption
- El usuario quiere un gancho más filoso para un borrador que ya tiene
- El usuario quiere un caption que se publique automáticamente con su contenido
  al aprobarlo

## Fórmulas que usa esta skill (formas centradas en el caption)

| Código | Fórmula | Objetivo principal | Ideal para |
|---|---|---|---|
| IG1 | Resultado con número adelante | guardados | un resultado de precisión poco redonda + una promesa de "cópialo" |
| IG2 | Verdad a contracorriente | compartidos | una afirmación filosa y defendible contra la corriente |
| IG3 | Apertura identificable | comentarios | un momento concreto y compartido, sin preámbulo |
| IG4 | Confesión en mini historia | comentarios, seguidores | una historia real en primera persona con un costo |

Esqueletos completos en `../../references/hook-formulas.md`. Para carruseles
(IG5-IG8) usa `ig-planificar-carrusel`; en los reels (IG9-IG10) el gancho está en
el video y esta skill escribe el caption que lo acompaña.

### Elige primero por objetivo

| Objetivo | Recurre a |
|---|---|
| Guardados | IG1 |
| Compartidos | IG2 |
| Comentarios | IG3, IG4 |
| Seguidores | IG4 |

## Pasos

**Primero el Perfil de voz (en todos los borradores).** Si `../../references/voice-profile.md` tiene `filled: yes`, cárgalo y respeta en todo el texto la huella de voz, las reglas estrictas, la variante de español y el estilo de llamada a la acción y de links del usuario. Si no está completo, menciona una vez que `ig-humanizar-texto --mode profile` puede aprender su voz a partir de algunos posts y sigue con las reglas de voz genéricas.

**Nunca inventes los datos concretos.** Las reglas de abajo piden un número concreto, una fecha y una entidad con nombre, porque eso es lo que separa un post real de uno generado. Tómalos de lo que el usuario dijo en esta conversación. **No inventes una cifra, una fecha, el nombre de un cliente ni un resultado, y no conviertas una afirmación vaga en un número de aspecto creíble.** Si el usuario no tiene nada concreto para un tramo, pregúntale una vez; si sigue sin tenerlo, quita la afirmación en lugar de adornarla. Un número inventado y publicado obliga a retractarse; uno ausente solo hace un post más débil.

1. **Reúne los datos.** Tema, enfoque, el contenido (imagen única o reel),
   audiencia objetivo y el objetivo (guardados / compartidos / comentarios /
   seguidores).
2. **Elige la fórmula.** Usa la tabla de objetivos para preseleccionar, luego
   propón 2-3 que también encajen con el tema y deja que el usuario elija.
3. **Escribe el gancho (primeros 125 caracteres).** Tiene que plantear la
   recompensa, la tensión o el número antes del corte de "más" y entenderse
   solo. Cuenta caracteres, no palabras: en español el texto ocupa más.
4. **Escribe el cuerpo.** Líneas cortas, espacio en blanco entre tramos, una sola
   idea. Enseña o cuenta la historia que prometió el gancho. Menos de 2.200
   caracteres.
5. **Escribe una sola llamada a la acción.** Una invitación concreta a guardar o
   enviar ("guárdalo para tu próximo lanzamiento", "envíaselo al amigo que
   siempre comete el error #2"), una pregunta real o un único paso siguiente.
   Nunca "¿qué opinas?".
6. **Agrega hashtags.** Pásale el tema a `ig-elegir-hashtags` o aplica tú
   mismo el set dimensionado de 3-5 (ver `../../references/hashtag-strategy.md`),
   priorizando hashtags en español. Ponlos al final o indica que van en el
   primer comentario.
7. **Pasada del humanizador.** Elimina el vocabulario de IA por densidad de
   párrafo, limita las rayas (alrededor de una cada 100 palabras; la única raya
   de un caption no es un indicio, nunca la reemplaces por punto), rompe tríadas
   apiladas, aperturas genéricas y puentes de revelación. Corrige solo un
   párrafo que suene plano como máquina; nunca fabriques variación ni líneas de
   una palabra para dar dramatismo. Agrega un número de precisión poco redonda
   con un referente nombrado o una entidad con nombre donde la afirmación lo
   permita. Revisa la ortografía (tildes, ¿ ¡). Reglas canónicas: `ig-humanizar-texto` V3.
8. **Auditoría opcional.** Invoca `ig-humanizar-texto --mode audit` para una
   verificación de aprobado/reprobado.
9. **Tarjeta de aprobación.** Muestra: fórmula usada, el gancho (indica si
   supera los 125 caracteres), caption completo, cantidad de caracteres, set de
   hashtags, objetivo principal y el contenido que el usuario debe aportar.
10. **Al aprobarse, publica con el contenido.** Llama a `lib.publish(kind="post",
    draft_text=<caption aprobado>, target_url="https://www.instagram.com/",
    media=[<rutas de archivos locales>], platforms=[<INSTAGRAM_PLATFORM_ID>],
    scheduled_time=<iso_o_None>)`. Para un reel pasa `kind="reel"`. El
    envoltorio ejecuta el flujo de Publora: borrador, subida y programación. Sin
    contenido o sin clave de Publora devuelve un bloque para copiar y pegar y un
    recordatorio de adjuntar el contenido.

## Reglas estrictas

Reglas de voz globales: ver la sección de reglas de voz del `SKILL.md` raíz.
Reglas adicionales propias de esta skill:

- Los primeros 125 caracteres tienen que frenar el scroll por sí solos. Reescribe
  todo gancho que necesite la segunda línea para entenderse.
- Una idea por caption. Dos ideas son dos posts.
- Un número concreto donde la afirmación lo permita.
- 3-5 hashtags dimensionados, nunca 30. 0-3 emojis, ubicados con intención.
- El contenido multimedia es obligatorio. Nunca presentes un caption como listo
  para publicar sin recordarle al usuario que adjunte la imagen o el video.
- No vendas a la fuerza. Como máximo, una mención natural del siguiente paso.

## Antipatrones (la skill se niega)

- Un gancho que solo se entiende después del corte.
- Rayas por encima del límite (más de una cada 100 palabras aproximadamente), o
  una raya reemplazada por punto.
- Aperturas como "Hablemos de.." o "Te cuento algo.."; "¿El resultado?" como
  revelación.
- Sinceridad anunciada ("hablemos claro", "no te voy a mentir", "POV:" sobre algo
  que no es un punto de vista) sin un hecho fechado que la respalde.
- Ráfagas entrecortadas ("Sin X. Sin Y. Solo Z.") y líneas de una palabra
  agregadas para dar dramatismo.
- 20-30 hashtags amontonados arriba.
- Cebo de interacción ("doble toque si estás de acuerdo", "comenta SÍ").
- Listas de tres sin datos concretos.
- "potenciar", "fundamental", "un antes y un después", "llevarlo al siguiente
  nivel", "sumérgete en".
- Inflar una idea de una línea para que parezca sustanciosa.

## Recursos

- `../../references/hook-formulas.md` - las 10 fórmulas de Instagram (IG1-IG4 son de caption)
- `../../references/algorithm-heuristics.md` - reglas de ranking de Instagram 2026
- `../../references/hashtag-strategy.md` - la receta de 3-5 hashtags dimensionados
- `../../references/media-workflow.md` - el flujo de borrador, subida y programación
- `references/caption-checklist.md` - la lista de limpieza y ajuste por caption

## Skills relacionadas

- `ig-planificar-carrusel` - cuando la idea es un carrusel slide por slide
- `ig-elegir-hashtags` - arma el set de hashtags dimensionado
- `ig-humanizar-texto` - limpia indicios de IA, más `--mode audit` para revisar
- `ig-extraer-gancho` - analiza el gancho de un post que admiras
