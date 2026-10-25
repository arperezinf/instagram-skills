# Flujo de publicación de contenido multimedia en Instagram

Instagram exige contenido multimedia en todos los posts. No existe un post de
Instagram solo de texto: la API lo rechaza. Por eso las skills de redacción de
este paquete producen el **caption, el gancho, los hashtags y el plan de slides
o de tomas**, y el **usuario aporta el archivo de imagen o video**. Publicar es
siempre un flujo multimedia.

## Contenido

- El flujo (nivel Publora)
- Reglas de contenedor (en qué se convierte la lista de archivos)
- Límites de archivos (al publicar)
- Nivel manual (sin Publora)
- Limpiar una subida fallida

## El flujo (nivel Publora)

Publicar en Instagram es un flujo de tres pasos. Crear un post con un
`scheduledTime` desde el principio hace competir al programador de Instagram con
la subida a S3, así que el orden es obligatorio:

```
1. POST /create-post          -> crear un BORRADOR (sin scheduledTime), obtener postGroupId
2. POST /get-upload-url       -> URL de S3 prefirmada para un archivo
   PUT  {uploadUrl}            -> subir los bytes del archivo a S3
   (repetir el paso 2 por cada imagen de un carrusel de 2-10 elementos, en el orden de las slides)
3. PUT  /update-post/:postGroupId  -> status="scheduled" + scheduledTime
```

En este paquete, `lib/publora_client.py` envuelve todo el flujo en un método:

```python
from lib import PubloraClient

client = PubloraClient()  # lee PUBLORA_API_KEY
result = client.publish_media_post(
    content="abajo te dejo la configuración en 3 pasos, cópiala\n\n#nicho #medio #amplio",
    platforms=["instagram-11223344"],   # INSTAGRAM_PLATFORM_ID
    media=["slide1.jpg", "slide2.jpg", "slide3.jpg"],  # rutas locales, en orden
    scheduled_time="2026-07-01T15:00:00.000Z",  # omitir para ~ahora
)
# -> {"postGroupId": ..., "media": [...], "scheduled": {...}}
```

O llama al envoltorio de alto nivel `publish()`, que deriva a manual / Publora /
diy y solo publica automáticamente cuando se pasan rutas de archivos:

```python
from lib import publish

publish(
    "carousel",
    draft_text="<caption aprobado>",
    target_url="https://www.instagram.com/",
    media=["slide1.jpg", "slide2.jpg", "slide3.jpg"],
    scheduled_time="2026-07-01T15:00:00.000Z",
)
```

Si algo falla después de crear el borrador, `publish_media_post` borra el
borrador para no dejar un grupo de posts roto con una subida abandonada.

## Reglas de contenedor (en qué se convierte la lista de archivos)

| Archivos aportados | Se convierte en | Notas |
|---|---|---|
| 1 imagen (JPEG/PNG/WebP) | un post de una foto | WebP se convierte automáticamente a JPEG |
| 2-10 imágenes | un carrusel, en el orden de la lista | sin mezclar formatos, todas imágenes |
| 1 video (MP4/MOV) | un reel por defecto | historia con `videoType: "STORIES"` |
| imágenes + video mezclados | rechazado | la API no permite carruseles mixtos |

Define la superficie con `platform_settings`:

```json
{ "platformSettings": { "instagram": { "videoType": "REELS" } } }
```

`videoType` es `"REELS"` (por defecto) o `"STORIES"`. El paquete lo define
automáticamente para `kind="reel"` y `kind="story"`.

## Límites de archivos (al publicar)

| Elemento | Límite |
|---|---|
| Formatos de imagen | JPEG, PNG, WebP (WebP se convierte a JPEG) |
| Tamaño máximo de imagen | 8 MB |
| Elementos de carrusel | 2-10 (API) |
| Duración de reel | hasta 3 min (180 s); 5-90 s aptos para la pestaña Reels |
| Tamaño de reel/video | 300 MB |
| Clip de video en carrusel | hasta 60 s |
| Relación de aspecto | de 4:5 vertical a 1,91:1 horizontal; 4:5 ocupa mejor el feed |
| Caption | 2.200 caracteres (los primeros ~125 visibles) |
| Tipo de cuenta | Empresa o Creador (las personales no son compatibles) |

## Nivel manual (sin Publora)

Sin `PUBLORA_API_KEY`, o cuando el usuario no indicó archivos a la skill, todas
las skills devuelven el caption aprobado como bloque para copiar y pegar, más un
recordatorio de adjuntar el contenido en la app de Instagram. Instagram igual
necesita la imagen o el video, así que el recordatorio no es opcional.

## Limpiar una subida fallida

Si una llamada a `get-upload-url` funciona pero falla el PUT a S3, el borrador
queda con una referencia rota que bloquea reprogramarlo. Borra el borrador
completo y empieza de nuevo:

```python
client.delete_post(post_group_id)   # DELETE /delete-post/:id
```

`publish_media_post` ya lo hace cuando algo falla.
