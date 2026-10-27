# Reglas de clasificación de ganchos (Instagram)

Extracción de características y heurísticas de puntaje que usa
`ig-extraer-gancho` para asignar un post a una de las 10 fórmulas de
`../../../references/hook-formulas.md`.

## Paso 1: detectar la superficie

| Señal | Superficie |
|---|---|
| Una foto + un caption | imagen única (mirar IG1-IG4) |
| 2-10 imágenes apiladas, puntos de deslizamiento | carrusel (mirar IG5-IG8) |
| Video vertical con audio | reel (mirar IG9-IG10) |

La URL ayuda: `/reel/` es un reel; `/p/` es una imagen única o un carrusel (los
puntos en la app los distinguen, así que pregúntale al usuario).

## Paso 2: extraer las características del gancho

### Ganchos de caption (primeros ~125 caracteres)

| Característica en la primera línea | Fórmula |
|---|---|
| Un número de precisión poco redonda + una promesa de "cópialo / así lo hice" | IG1 Resultado con número adelante |
| Una afirmación sin rodeos que contradice el consejo habitual | IG2 Verdad a contracorriente |
| Un momento concreto y compartido, sin preámbulo ni número | IG3 Apertura identificable |
| Una marca temporal en primera persona + un costo o sorpresa admitidos | IG4 Confesión en mini historia |

### Ganchos de carrusel (slide 1 + estructura)

| Característica | Fórmula |
|---|---|
| La slide 1 promete N elementos numerados; el cuerpo es un elemento por slide | IG5 Lista |
| La slide 1 muestra un "después"; la slide 2 el "antes"; el cuerpo son pasos | IG6 Antes/después |
| Las slides del cuerpo emparejan "Mito:" con "Verdad:" | IG7 Derriba mitos |
| La slide 1 nombra un marco; la última lo resume en una slide | IG8 Marco de trabajo para copiar |

### Ganchos de reel (primeros 1-3 segundos)

| Característica | Fórmula |
|---|---|
| Ruptura de patrón / texto en pantalla con bucle abierto, sin introducción lenta | IG9 Rompe el patrón |
| "Cómo {resultado} en {plazo}" + pasos etiquetados | IG10 Cómo lo hice |

## Paso 3: puntuar la confianza

- **Alta (0,8 o más):** el gancho coincide limpiamente con el esqueleto de una
  fórmula y el cuerpo sigue su estructura.
- **Media (0,5-0,8):** el gancho encaja pero el cuerpo es suelto, o dos fórmulas
  se superponen (es común: IG1 e IG10 usan resultado + pasos). Devuelve las 2
  primeras.
- **Baja (menos de 0,5):** no hay coincidencia limpia. Describe la estructura
  literalmente y sugiere la fórmula más cercana como punto de partida.

Cuando encajan dos, el desempate es el **objetivo principal** (abajo) y la
superficie: un resultado solo en caption es IG1; el mismo resultado como reel con
pasos es IG10.

## Paso 4: nombrar el objetivo principal

Deduce para qué se optimizó el original a partir de su estructura y su cierre:

| Cierre / estructura | Objetivo probable |
|---|---|
| "guárdalo", una lista, un marco, un tutorial | guardados |
| "envíaselo a..", una recompensa a contracorriente o de mito | compartidos |
| un momento identificable, una pregunta, una confesión | comentarios |
| prueba de transformación, "sígueme para.." | seguidores |

## Paso 5: armar la plantilla en blanco

Copia el esqueleto de la fórmula elegida desde `../../../references/hook-formulas.md`,
mantén su estructura de espacios y renombra los espacios según el tema del
usuario. Quita los indicios de IA que tenía el original (no traslades a la
plantilla una acumulación de vocabulario de IA ni un bloque de 30 hashtags; una
sola raya en el original está bien). Si el original está en inglés, adapta la
plantilla a una construcción natural en español, no un calco.

## Paso 6: auditar la fuente

Señala, para que el usuario no lo copie:
- rayas por encima de aproximadamente una cada 100 palabras; guiones entre oraciones
- una acumulación de vocabulario de IA (3 o más marcadores en un párrafo:
  potenciar, fundamental, cabe destacar, elevar; o en inglés leverage,
  fundamentally, significant, elevate)
- 20-30 hashtags amontonados arriba
- cebo de interacción ("comenta SÍ", "etiqueta a 3 amigos")
- un gancho que solo se entiende después del corte de "más"
