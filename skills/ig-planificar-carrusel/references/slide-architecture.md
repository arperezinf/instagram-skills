# Arquitectura de slides del carrusel

Las columnas por fórmula y las reglas del texto sobre la imagen que usa
`ig-planificar-carrusel`. Un carrusel tiene 2-10 slides (límite de la API; la app
nativa permite 20). Diseña para el formato vertical 4:5, que ocupa la mayor
parte de la pantalla.

## La columna universal

| Slide | Función | Texto sobre la imagen |
|---|---|---|
| 1 (gancho) | promesa + bucle abierto | una idea grande, 6-14 palabras, un número si encaja |
| 2 | el valor más fuerte | el mejor punto individual, adelantado |
| 3 a N-1 | una idea cada una | corto, se entiende solo, legible en 2 segundos |
| N (recompensa) | resumen para guardar + un pedido | el resumen en una slide, luego guardar/seguir |

El deslizamiento cae con la profundidad, así que el orden del valor importa más
que la cantidad. Pon el mejor punto en la slide 2 o 3, nunca en la 10.

## Reglas del texto sobre la imagen

- **Una idea por slide.** Si una slide necesita dos pensamientos, divídela.
- **Legible en 2 segundos.** Texto grande, pocas palabras. La slide es un cartel,
  no un párrafo. El detalle va en la descripción.
- **Numera las slides** cuando el formato es una lista (slide 2 = "1.", etc.)
  para que el bucle abierto ("la mayoría se pierde la #4") se cumpla.
- **Coherencia visual.** Misma tipografía, mismos márgenes y mismo color de
  acento en todas las slides, para que se lea como un conjunto.
- **Rayas limitadas a una por slide** en el texto sobre la imagen, y solo cuando
  cumplen una función real (una slide casi nunca la necesita). El carácter no es
  un indicio en 2026; una slide pegada a fuerza de rayas sí lo es. Reemplaza el
  exceso por dos puntos o un salto de línea, nunca por punto.
- **El español ocupa más que el inglés.** Prefiere palabras cortas y verbos
  directos; evita nominalizaciones ("la implementación de") que alargan la línea.

## IG5 - Carrusel de lista (objetivo: guardados)

```
Slide 1: {N} {cosas} que {recompensa}. (la mayoría se pierde la #{k})
Slide 2: 1. {elemento} + un ejemplo concreto
Slide 3: 2. {elemento} + ejemplo
...
Slide N-1: {N}. {elemento} + ejemplo
Slide N: la lista resumida en una slide + "guárdalo para usarlo"
```

Pon el elemento más sorprendente en la posición 1 o 2 de la lista, no al final.

## IG6 - Transformación antes/después (objetivo: guardados, seguidores)

```
Slide 1: {el después, con un número o una imagen impactante}
Slide 2: dónde empezó (el antes): el bucle abierto es la distancia
Slide 3 a N-1: los pasos exactos, uno por slide
Slide N: el resultado repetido + "sígueme para ver el sistema completo de {tema}"
```

La distancia entre el antes y el después en las slides 1 y 2 es lo que impulsa
el deslizamiento. Los pasos tienen que ser lo bastante concretos para hacerlos
mañana.

## IG7 - Derriba mitos (objetivo: compartidos)

```
Slide 1: {N} mitos sobre {tema} que te están costando {pérdida concreta}
Slide 2 a N-1: "Mito: {creencia}" y luego "Verdad: {lo que funciona}"
Slide N: el replanteo en una línea + "envíaselo a alguien que todavía cree en el #1"
```

La invitación a enviar en la última slide es el punto central; los derriba mitos
se envían.

## IG8 - Marco de trabajo para copiar (objetivo: guardados)

```
Slide 1: el marco {nombre} que uso para {resultado}
Slide 2 a N-1: una parte del marco por slide, con el porqué
Slide N: el marco completo en una slide (lo que se guarda) + invitación a guardar
```

El resumen en una sola slide es lo que la gente guarda. Haz que se entienda solo.

## Guía de cantidad de slides

| Contenido | Slides |
|---|---|
| Una lista o marco ajustado | 6-8 |
| Un conjunto educativo más rico o una transformación | 8-10 |
| Menos de 4 puntos reales | publícalo como imagen única |

Nunca rellenes hasta 10. Una idea de 5 puntos es un carrusel de 5 puntos (7
slides con gancho y recompensa), no uno de 10 inflado.

## Combinación con la descripción

En un carrusel la descripción puede ser corta porque las slides llevan el contenido.
Debe: repetir el gancho para el corte de "más", agregar una línea de contexto,
llevar la llamada a la acción y los 3-5 hashtags dimensionados. Ver
`../../../references/hashtag-strategy.md`.
