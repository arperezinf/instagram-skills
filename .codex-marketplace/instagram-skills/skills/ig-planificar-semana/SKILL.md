---
name: ig-planificar-semana
description: "Genera en español un plan semanal de Instagram a partir de un tema, una audiencia y pilares de contenido. Produce una mezcla diaria de reels, carruseles, imágenes e historias, cada uno con fórmula de gancho, enfoque, horario y objetivo, más una meta semanal de guardados y compartidos (la palanca 2026), un ritmo de historias y un control de equilibrio entre objetivos. No para redactar una descripción (usa ig-redactar-descripcion) ni un carrusel (usa ig-planificar-carrusel)."
---

# Planificador de contenido para Instagram

Produce un plan semanal de Instagram basado en una disciplina de pilares y en la
mezcla de formatos que premia Instagram: reels para el alcance, carruseles para
los guardados, historias para la relación. El plan fija una meta semanal de
guardados y compartidos, porque los envíos por alcance y los guardados son las
palancas de 2026.

El plan y todos los enfoques se escriben en español neutro, salvo que el Perfil
de voz indique otra variante.

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

- El usuario pide "planifica mi semana en Instagram" o "¿qué publico esta semana?"
- El usuario quiere dejar de publicar improvisando y establecer un ritmo
- Antes de una semana de lanzamiento (el plan alinea un pilar de producto)

## Entrada

- **Tema** (opcional): por ejemplo "lanzamiento de nuestro curso de diseño"
- **Descripción de la audiencia:** por ejemplo "diseñadores junior, personas que
  cambian de carrera"
- **Mezcla de pilares** (opcional): por defecto 40% Educativo / 30% Historia /
  20% Interacción / 10% Promoción
- **Ritmo de publicación** (opcional): por defecto 4-5 posts de feed por semana
  + historias diarias
- **Zona horaria de la audiencia** (opcional pero recomendada)
- **Muestras de voz** (opcional): descripciones anteriores para calibrar la voz

## Salida

Un plan en markdown con:

### Calendario de 7 días

| Día | Formato | Pilar | Fórmula | Enfoque en una línea | Objetivo | Horario |
|---|---|---|---|---|---|---|
| Lun | Reel | Educativo | IG9 Rompe el patrón | "publicas tus reels en el peor horario" | compartidos | 12:00 |
| Mar | Carrusel | Educativo | IG5 Lista | "7 errores de portafolio" | guardados | 11:30 |
| Mié | Serie de historias | Interacción | encuesta + pregunta | "¿qué diseño gana?" | comentarios | 19:00 |
| Jue | Carrusel | Historia | IG6 Antes/después | "de mis primeros 0 USD a los primeros 4.000 USD" | seguidores | 11:00 |
| Vie | Imagen única | Interacción | IG3 Identificable | "abrir Canva para un solo diseño" | comentarios | 13:00 |
| Sáb | Reel | Educativo | IG10 Cómo lo hice | "cómo edito un reel en 20 minutos" | guardados | 10:00 |
| Dom | Serie de historias | Promoción | republicación + link | "abrimos inscripciones" | seguidores | 18:00 |

(La skill completa los enfoques reales a partir del tema; los números del
ejemplo son ilustrativos. Las historias se publican todos los días, además de
los posts del feed).

### Meta semanal de guardados

- Fija una **meta concreta de guardados + compartidos** para la semana (la
  palanca principal). Heurística por defecto: al menos 3 de los posts de feed de
  la semana son formatos que invitan a guardar (IG1, IG5, IG6, IG8, IG10) y al
  menos 2 invitan a enviar (IG2, IG7, IG9).
- Mide guardados y compartidos como métrica principal, no los "me gusta".

### Ritmo diario de historias

- 2-4 cuadros de historia por día: detrás de escena, un sticker de encuesta o
  pregunta y al menos una republicación de un post reciente del feed (una señal
  equivalente a un envío que lleva el post a seguidores que no lo vieron).
- Las historias profundizan la relación con los seguidores; no persiguen alcance
  entre no seguidores.

### Control de equilibrio semanal

- [ ] Mezcla de formatos: al menos 2 reels (alcance), al menos 2 carruseles (guardados), historias diarias
- [ ] Al menos 3 posts que invitan a guardar y 2 que invitan a enviar
- [ ] Al menos 1 post de historia real en primera persona (genera confianza y seguidores)
- [ ] Ningún pilar supera el 50% de los posts de feed de la semana
- [ ] Ninguna fórmula se repite más de dos veces en la semana
- [ ] Pilar de promoción: 1-2 posts como máximo
- [ ] Objetivos repartidos entre guardados, compartidos, comentarios y seguidores

## Mezcla de objetivos (equilibrar la semana)

Cada fórmula consigue una señal principal. Una semana hecha solo de cebo de
guardado o solo de contenido identificable se lee como fabricada. Reparte los
objetivos:

| Objetivo | Fórmulas | Meta semanal |
|---|---|---|
| Guardados | IG1, IG5, IG6, IG8, IG10 | al menos 3 (la palanca principal) |
| Compartidos | IG2, IG7, IG9 | al menos 2 |
| Comentarios | IG3, IG4 | al menos 1 |
| Seguidores | IG4, IG6, IG8 | al menos 1 |

## Reglas

- **La constancia le gana a la frecuencia.** 4-5 posts de feed de calidad por
  semana con historias diarias rinden más que un volcado diario de relleno. No
  rellenes para llegar a una cantidad.
- **Reels para el alcance, carruseles para los guardados, historias para la
  relación.** Usa la superficie correcta para cada tarea.
- **Los reels se pueden publicar más seguido** que los carruseles sin saturar,
  porque cada uno llega a una audiencia nueva de no seguidores.
- **Horarios:** las franjas de referencia publicadas (días de semana 11-13 h y
  19-21 h, más el domingo por la tarde-noche) provienen de datos de audiencias
  de EE. UU. Para audiencias hispanohablantes no hay datos equivalentes en este
  paquete: usa la zona horaria de la audiencia, toma esas franjas solo como
  punto de partida y recomienda ajustarlas con las estadísticas de Instagram del
  usuario. Nunca presentes un horario como dato medido si no lo es.
- **Pilar de promoción: máximo 1-2 posts por semana.** Usarlo de más entierra el
  alcance.
- **Una fórmula por espacio, variada a lo largo de la semana.** No apiles tres
  carruseles IG5.

## Fórmula -> pilar

| Pilar | Fórmulas preferidas |
|---|---|
| Educativo | IG5 Lista, IG8 Marco de trabajo, IG10 Reel "cómo lo hice", IG1 Número adelante |
| Historia | IG4 Confesión, IG6 Antes/después |
| Interacción | IG3 Identificable, IG9 Reel que rompe el patrón, stickers de historias |
| Promoción | IG6 (resultados que implican el producto), IG1 (tus propios datos) |

## Pasos

1. Reúne los datos. Pide tema, audiencia, zona horaria y preferencias de pilares
   si no se indicaron.
2. Verifica que la mezcla de pilares sume 100%; advierte si algún pilar supera
   el 50%.
3. Para cada día, elige: formato (reel/carrusel/imagen/historia), pilar,
   fórmula (sin repetir de más), enfoque, horario (en la zona horaria de la
   audiencia, formato de 24 horas) y objetivo.
4. Fija la meta semanal de guardados + compartidos y el ritmo diario de historias.
5. Ejecuta el control de equilibrio semanal y el de mezcla de objetivos; señala
   lo que falte.
6. Devuélvelo en markdown, más un JSON opcional para importar.

## Ejemplo

Ver `references/example-week.md` para un plan de 7 días completo.

## Archivos

- `SKILL.md` - este archivo
- `references/example-week.md` - plan de 7 días completo
- `references/pillars-framework.md` - la disciplina de pilares de Instagram explicada

## Skills relacionadas

- `ig-redactar-descripcion` - redacta la descripción de cada imagen única del plan
- `ig-planificar-carrusel` - redacta cada carrusel del plan
- `ig-elegir-hashtags` - rota sets de hashtags dimensionados a lo largo de la semana
- `ig-extraer-gancho` - estudia posts de la competencia mientras planificas
