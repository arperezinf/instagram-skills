---
name: ig-planificar-carrusel
description: "Planifica en español un carrusel de Instagram slide por slide, hasta 10, con una slide de gancho que abre un bucle, slides de valor que adelantan la recompensa y una slide final que consigue guardado y seguimiento. Elige una fórmula 2026 (lista, antes/después, derriba mitos, marco de trabajo) por objetivo, redacta el texto de cada slide y el caption, y publica tus imágenes vía Publora. No para captions de una sola imagen (usa ig-redactar-caption)."
---

# Planificador de carruseles para Instagram

Planifica un carrusel que se deslice hasta el final y se guarde. Todo el juego
está en la slide 1 (el gancho que consigue el deslizamiento) y en la última (la
recompensa que se guarda). Esta skill arma el mapa de cada slide, escribe el
texto sobre la imagen y redacta el caption que lo acompaña.

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

- El usuario quiere convertir un tema o unas notas en un carrusel de varias slides
- El usuario tiene una lista, un marco de trabajo o una transformación para enseñar
- El usuario quiere una estructura slide por slide, no solo un caption

## Fórmulas que usa esta skill (formas de carrusel)

| Código | Fórmula | Objetivo principal | Ideal para |
|---|---|---|---|
| IG5 | Carrusel de lista | guardados | una lista educativa numerada, un elemento por slide |
| IG6 | Transformación antes/después | guardados, seguidores | prueba de un resultado con los pasos intermedios |
| IG7 | Derriba mitos | compartidos | corregir creencias de tu nicho |
| IG8 | Marco de trabajo para copiar | guardados | un marco con nombre y repetible |

Esqueletos completos en `../../references/hook-formulas.md`.

## Arquitectura de slides (la columna de 10 slides)

Un carrusel tiene 2-10 slides (límite de la API). La columna confiable:

| Slide | Función |
|---|---|
| **1 (gancho)** | la promesa + un bucle abierto ("la mayoría se pierde la #4"). Consigue el deslizamiento. Texto grande, una idea. |
| **2-3** | el valor más fuerte, adelantado (el deslizamiento cae con la profundidad). |
| **4 a N-1** | una idea por slide, cada una se entiende sola y se lee en 2 segundos. |
| **N (recompensa)** | el resumen en una slide (lo que se guarda) + un único pedido claro (guardar / seguir). |

6-10 slides es el punto justo para un carrusel educativo. Menos de 4 suele ser
una imagen única. Ver `references/slide-architecture.md` para las columnas de
cada fórmula.

## Pasos

**Primero el Perfil de voz (en todos los borradores).** Si `../../references/voice-profile.md` tiene `filled: yes`, cárgalo y respeta en todo el texto la huella de voz, las reglas estrictas, la variante de español y el estilo de llamada a la acción y de links del usuario. Si no está completo, menciona una vez que `ig-humanizar-texto --mode profile` puede aprender su voz a partir de algunos posts y sigue con las reglas de voz genéricas.

**Nunca inventes los datos concretos.** Las reglas de abajo piden un número concreto, una fecha y una entidad con nombre, porque eso es lo que separa un post real de uno generado. Tómalos de lo que el usuario dijo en esta conversación. **No inventes una cifra, una fecha, el nombre de un cliente ni un resultado, y no conviertas una afirmación vaga en un número de aspecto creíble.** Si el usuario no tiene nada concreto para un tramo, pregúntale una vez; si sigue sin tenerlo, quita la afirmación en lugar de adornarla. Un número inventado y publicado obliga a retractarse; uno ausente solo hace un post más débil.

1. **Reúne los datos.** Tema, la lista / marco / transformación, audiencia
   objetivo y el objetivo (guardados / compartidos / seguidores).
2. **Elige la fórmula.** Usa la tabla de objetivos; propón 2-3 que encajen y
   deja que el usuario elija.
3. **Define la cantidad de slides.** Que coincida con el contenido real (6-10 es
   lo típico). Nunca rellenes para llegar a 10; se nota el relleno y abandonan.
4. **Escribe la slide 1.** La promesa más el bucle. Texto grande sobre la imagen,
   una sola idea. Adelanta un número si encaja.
5. **Arma las slides de valor.** Pon el punto más fuerte en la slide 2 o 3. Una
   idea por slide, cada una se entiende sola. Redacta el texto sobre la imagen
   de cada una (corto: tiene que leerse en 2 segundos en un formato 4:5; en
   español el texto ocupa más, así que recorta palabras).
6. **Escribe la slide final.** Un resumen en una slide que valga la pena
   guardar por sí solo, más un único pedido (guárdalo / sígueme para más).
7. **Escribe el caption.** El caption acompaña al carrusel (puede ser corto),
   repite el gancho para el corte y lleva los hashtags. Pásalo a
   `ig-elegir-hashtags` o aplica el set dimensionado de 3-5.
8. **Pasada del humanizador** sobre el texto de las slides y el caption. Elimina
   el vocabulario de IA por densidad (por slide, por párrafo del caption),
   limita las rayas (como máximo una por slide, alrededor de una cada 100
   palabras en el caption; nunca reemplaces una por punto), rompe tríadas
   apiladas y puentes de revelación. Las slides son cortas por diseño: nunca
   cortes ni rellenes una slide por ritmo. Revisa la ortografía. Reglas
   canónicas: `ig-humanizar-texto` V3.
9. **Tarjeta de aprobación.** Muestra: fórmula, el esquema slide por slide con
   el texto de cada una, el caption, el set de hashtags, el objetivo principal y
   un recordatorio de que el usuario aporta 2-10 imágenes (todas imágenes, sin
   mezclar formatos) en este orden.
10. **Al aprobarse, publica con el contenido.** Llama a `lib.publish(kind="carousel",
    draft_text=<caption aprobado>, target_url="https://www.instagram.com/",
    media=[<rutas de las imágenes en orden>], platforms=[<INSTAGRAM_PLATFORM_ID>],
    scheduled_time=<iso_o_None>)`. El envoltorio sube cada imagen en orden y
    programa. Sin contenido o sin clave de Publora devuelve el plan como bloque
    para copiar y pegar más el orden de las slides.

## Reglas estrictas

Reglas de voz globales: ver la sección de reglas de voz del `SKILL.md` raíz.
Reglas adicionales propias de esta skill:

- La slide 1 es una promesa con un bucle abierto, nunca un título pelado.
- El valor va adelante, en las slides 2-3; nunca entierres el mejor punto al final.
- Una idea por slide, legible en 2 segundos en un formato vertical 4:5.
- Solo 2-10 slides. Nunca rellenes para llegar a un número redondo.
- Todo imágenes, sin mezclar formatos (la API rechaza un carrusel de imagen + video).
- La última slide tiene que conseguir el guardado con un resumen en una slide y
  un único pedido.

## Antipatrones (la skill se niega)

- Una slide 1 que es solo título, sin promesa ni bucle.
- Un carrusel de 10 slides inflado a partir de una idea de 4 puntos.
- El punto más fuerte guardado para la última slide.
- Tres llamadas a la acción compitiendo en la slide final.
- Mezclar imágenes y un video en un mismo carrusel.
- Bloques de texto sobre la imagen que no se pueden leer al deslizar.
- Rayas por encima del límite (más de una por slide), acumulación de vocabulario
  de IA, tríadas apiladas o huecas.
- Revelaciones del tipo "¿El resultado?" y ráfagas entrecortadas agregadas para
  dar golpe.

## Recursos

- `../../references/hook-formulas.md` - las fórmulas de carrusel (IG5-IG8) con esqueletos
- `../../references/algorithm-heuristics.md` - ranking de carruseles 2026 y reglas de deslizamiento
- `../../references/hashtag-strategy.md` - la receta de 3-5 hashtags dimensionados
- `../../references/media-workflow.md` - subir 2-10 imágenes en orden
- `references/slide-architecture.md` - columnas por fórmula y reglas del texto sobre la imagen

## Ilustración opcional

Ofrece una imagen generada cuando un visual pueda subir el alcance. Redacta un
prompt y llama a `lib.illustrate(prompt, kind="carousel")`, tomando el usuario y
el color de marca de la sección 6 del Perfil de voz y marca para una
superposición exacta al píxel. Muestra la `url` y el `cost` devueltos y
adjúntala como contenido de Instagram con `media_urls=[url]` en un solo paso
(Publora descarga la URL alojada desde su servidor): una imagen se publica como
foto, y el planificador de carruseles puede pasar 2-10 URLs para un carrusel.
Para la portada de un reel, define `platformSettings.instagram.coverUrl`. Flujo
completo (incluidas las tarjetas de cita): `../ig-humanizar-texto/sub-skills/illustration.md`.
Sin clave de Pixfaro, redacta el prompt para que generes la imagen manualmente.
Escribe en español el texto que vaya sobre la imagen.

## Skills relacionadas

- `ig-redactar-caption` - cuando la idea es una imagen única, no un carrusel
- `ig-elegir-hashtags` - arma el set de hashtags dimensionado
- `ig-humanizar-texto` - limpia el texto de las slides y el caption
- `ig-extraer-gancho` - analiza un carrusel que admiras
