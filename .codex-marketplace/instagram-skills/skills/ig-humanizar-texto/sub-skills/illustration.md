# Sub-skill: generar una ilustración para un post de Instagram

Agrega una imagen opcional a un borrador (imagen de feed, slide de carrusel o
tarjeta de cita) y la adjunta al publicar. Usa la capa de imágenes de Pixfaro a
través de `lib.illustrate`, que devuelve una URL alojada que pasa directo al
contenido de Publora. Funciona en cualquier agente (Claude Code, Codex,
OpenClaw).

## Cuándo se ejecuta

- El usuario dice "agrega una imagen", "haz una ilustración", "haz una tarjeta
  de cita" o "haz un carrusel" para un post de Instagram.
- Ofrécelo una vez después de aprobar un borrador, cuando un visual pueda subir
  el alcance.

## Backends (replican la capa de publicación)

- **pixfaro** - `PIXFARO_TOKEN` (`pf_live_...`) definido: la imagen se genera y
  se adjunta automáticamente.
- **manual** - sin token: la skill redacta el prompt de la imagen y le pide al
  usuario que la genere y pegue la URL. Nunca bloquea un borrador.

`lib.image_backend()` informa cuál está activo.

## Pasos

1. **Elige el tipo.** El predeterminado para Instagram es `carousel` (aspecto
   4:5). Cámbialo con `aspect_ratio="w:h"` cuando haga falta. Otros tipos:
   thumbnail 16:9, carousel/quote/portrait 4:5, story/cover 9:16, wide/link
   16:9, square 1:1.
2. **Redacta el prompt.** Describe el sujeto, la composición, el estilo y la
   paleta. Por defecto, un aspecto limpio y profesional salvo que la §6 del
   Perfil de voz y marca defina un estilo visual. NO metas las palabras del post
   dentro del arte (usa la superposición). El prompt puede ir en inglés si el
   modelo responde mejor así, pero todo texto visible en la imagen va en español.
3. **Aplica la superposición de marca (si el perfil la tiene).** Lee la §6 de
   `../../../references/voice-profile.md`. Si hay usuario, color de marca o logo,
   pasa un `overlay` para que el texto o el logo se compongan exactos al píxel
   (nítidos incluso con un modelo barato):
   ```python
   from lib import illustrate
   r = illustrate("<prompt de la escena>", kind="carousel",
                  overlay={"text": "@usuario", "position": "bottom-right", "color": "#RRGGBB"})
   ```
   Para una **tarjeta de cita**, pon la línea del gancho en el `text` del overlay
   (no en el prompt), con `kind="quote"`. Verifica que la tipografía muestre bien
   tildes, eñes y signos de apertura.
4. **Elección de modelo.** Por defecto `nano-banana-2`. La superposición maneja
   el texto, así que un modelo base barato está bien; recurre a
   gemini-pro-image solo para arte premium. Nunca subas de nivel en silencio.
5. **Muestra y confirma.** Presenta la `url` y el `cost` devueltos. Al
   aprobarse, adjúntala con `media_urls=[r["url"]]` al publicar.
6. **Modo manual.** Si `r["backend"] == "manual"`, muestra `r["message"]` y pide
   una URL pegada.

## Refinar en lugar de regenerar

Cuando el usuario quiere un ajuste ("oscurece el cielo", "cambia el titular",
"más espacio en blanco"), NO regeneres desde cero. Conserva el `id` del
resultado anterior y edítalo:

```python
from lib import illustrate, refine
first = illustrate("<escena>", kind="wide")     # -> {"id": "img_...", "url": ...}
fixed = refine(first["id"], "oscurece el fondo y aumenta el contraste")
```

`refine` edita por id `img_...` (no por URL), hereda la forma y el nivel de la
fuente cuando omites `aspect_ratio`/`resolution`, y es más barato y más
coherente que una generación nueva. Encadénalo todas las veces que haga falta.

## Control de costos

- Cada resultado trae `cost` y `balance_after`; si `low_balance` es True, avísale
  al usuario que el saldo de Pixfaro está bajo antes de generar más.
- Por defecto `nano-banana-2` + 1K. Los modelos premium (`gemini-pro-image`,
  `gpt-5-image`) cobran varias veces más: úsalos solo cuando el usuario los pida
  por nombre; `illustrate`/`refine` nunca suben de nivel por su cuenta. La marca
  `premium` de un resultado es True cuando se usó un modelo de precio premium:
  confirma que era lo buscado.
- `lib.available_models()` devuelve precios y latencias en vivo cuando necesites
  mostrarlos.

## Reglas estrictas

- Una imagen por pedido (`n>1` no está soportado); genera las slides de un
  carrusel de a una.
- Las palabras reales van en el `overlay`, no dentro del arte del prompt.
- Por defecto el modelo barato + resolución 1K, salvo que el usuario pida premium.
- Nunca adjuntes una imagen que el usuario no haya visto y aprobado.
