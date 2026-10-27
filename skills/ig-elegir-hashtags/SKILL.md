---
name: ig-elegir-hashtags
description: "Arma un set dimensionado de hashtags para un post de Instagram según la realidad 2026: 3 a 5 bien elegidos le ganan a 30 al azar. Clasifica cada etiqueta como nicho (menos de 50 mil posts), media (50 a 500 mil) o amplia (más de 500 mil) y arma una mezcla de 2-3 nicho, 1-2 medias y 0-1 amplia donde una cuenta chica pueda posicionarse, priorizando el español y rotando para evitar spam. No para escribir el caption (usa ig-redactar-caption)."
---

# Estratega de hashtags para Instagram

Elige 3-5 hashtags que de verdad ayuden, dimensionados para que el post pueda
posicionarse. El muro de 30 etiquetas murió: en 2026 los hashtags funcionan como
etiquetas de tema, y una cuenta chica se posiciona en etiquetas de nicho, no en
las amplias de millones de posts. Esta skill arma el set dimensionado.

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

- El usuario tiene un caption, carrusel o reel y necesita hashtags
- El usuario todavía publica 20-30 etiquetas genéricas y quiere el enfoque 2026
- El usuario quiere etiquetas dimensionadas según dónde su cuenta puede posicionarse

## El modelo: tamaño, no volumen

El **tamaño** de una etiqueta es su cantidad total de posts. La estrategia es una
mezcla para que el post se posicione en las etiquetas chicas mientras toca las
más grandes.

| Nivel | Cantidad de posts | Función | Uso |
|---|---|---|---|
| Nicho | menos de 50 mil | donde una cuenta chica o mediana puede posicionarse durante horas | 2-3 |
| Medio | 50 mil - 500 mil | audiencia suficiente, competencia superable | 1-2 |
| Amplio | más de 500 mil | un breve toque de etiqueta de categoría, se posiciona por minutos | 0-1 |

**Por defecto: 3-5 en total.** El razonamiento completo está en
`../../references/hashtag-strategy.md`.

## Idioma de los hashtags

- Para una audiencia hispanohablante, propone hashtags en español primero.
- No asumas que la traducción de una etiqueta inglesa tiene el mismo tamaño;
  clasifícala de nuevo y pide verificarla en la app.
- Revisa variantes con y sin tilde o eñe (`#diseño` / `#diseno`): Instagram las
  trata como etiquetas distintas. Indica cuál conviene verificar.
- Usa etiquetas en inglés solo si la audiencia es bilingüe o el término se usa
  así en el nicho (por ejemplo `#ux`).

## Pasos

1. **Obtén el post.** El caption, el tema del carrusel o el asunto del reel, más
   la audiencia objetivo y el tamaño aproximado de la cuenta (para que la
   división nicho/medio encaje).
2. **Extrae los temas.** Saca los 3-5 temas reales del post (el asunto, la
   comunidad de nicho, el formato, el resultado).
3. **Genera candidatas por nivel.** Para cada tema, propone candidatas de nicho,
   medias y amplias. Las de nicho son específicas y de cola larga
   (`#notionparafreelancers`); las amplias son palabras comunes sueltas
   (`#marketing`).
4. **Dimensiona cada candidata.** Estima el nivel por especificidad (la API no
   expone conteos, así que usa criterio y pídele al usuario que verifique los
   conteos en el buscador de la app). Señala para descartar toda etiqueta
   obviamente genérica o propensa a ser marcada (`#follow4follow`,
   `#like4like`, `#sigoatodos`).
5. **Arma el set.** 2-3 de nicho + 1-2 medias + 0-1 amplia, total 3-5. Quita la
   amplia si ninguna encaja de verdad. Cada etiqueta tiene que coincidir con el
   contenido.
6. **Verifica la coincidencia.** Rechaza toda etiqueta popular pero fuera de
   tema; un desajuste entrena mal al motor de recomendación y baja el alcance.
7. **Rota.** Indícale al usuario que varíe el set según el tema y que no reutilice
   un mismo bloque en todos los posts (sets idénticos en muchos posts se leen
   como automatización).
8. **Entrega.** El set de 3-5, cada etiqueta con su nivel y una línea de por qué,
   más la indicación de ubicación (final del caption o primer comentario).

## Formato de salida

```
Set dimensionado (4 etiquetas):
  #notionparafreelancers   nicho    la comunidad exacta a la que sirve este post
  #flujodetrabajofreelance nicho    cola larga, se renueva despacio, posicionable
  #productividad           medio    audiencia tibia y relevante, superable
  #notion                  amplio   etiqueta de categoría, un solo toque

Ubicación: al final del caption o en el primer comentario. Rota las de nicho según el tema.
Verifica en el buscador de la app el conteo de cada etiqueta antes de publicar.
```

Los niveles del ejemplo son estimaciones ilustrativas, no conteos verificados.

## Reglas estrictas

Reglas de voz globales: ver la sección de reglas de voz del `SKILL.md` raíz.
Reglas adicionales propias de esta skill:

- 3-5 etiquetas en total. Nunca entregues un bloque de 30.
- Cada etiqueta tiene que describir el contenido real. Sin etiquetas populares
  pero fuera de tema.
- Como máximo una etiqueta amplia; quítala si ninguna encaja.
- Señala y elimina etiquetas de granja de interacción (`#follow4follow`,
  `#like4like`) y cualquier etiqueta marcada conocida.
- Los hashtags van al final del caption o en el primer comentario, nunca a mitad
  de una oración.
- Rota los sets según el tema; no le des al usuario un bloque para pegar siempre.
- Nunca presentes un conteo de posts como verificado si no lo viste; marca las
  estimaciones como tales.

## Antipatrones (la skill se niega)

- Entregar 20-30 hashtags.
- Un "paquete de hashtags virales" de etiquetas amplias y genéricas.
- Etiquetas que no coinciden con el post para perseguir una audiencia más grande.
- Esconder 30 etiquetas detrás de puntos para que "se vea limpio".
- Sets solo de etiquetas amplias en las que una cuenta chica no puede posicionarse.

## Recursos

- `../../references/hashtag-strategy.md` - el modelo de dimensionamiento 2026 completo y la receta
- `../../references/algorithm-heuristics.md` - por qué los envíos y guardados, no los feeds de hashtags, impulsan el alcance
- `references/sourcing-tactics.md` - cómo encontrar y dimensionar candidatas

## Skills relacionadas

- `ig-redactar-caption` - escribe el caption al que se suman los hashtags
- `ig-planificar-carrusel` - el carrusel cuyo caption lleva el set
- `ig-planificar-semana` - rota los temas de etiquetas a lo largo de la semana
