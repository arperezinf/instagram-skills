# Convenciones del proyecto - instagram-skills (versión en español)

Este archivo es para cualquier agente de Claude Code que trabaje en este
repositorio. Léelo antes de hacer cambios. Estas convenciones son obligatorias
salvo que el usuario pida otra cosa.

Este repositorio es un fork traducido y adaptado al español de
[sergebulaev/instagram-skills](https://github.com/sergebulaev/instagram-skills).

## Idioma y traducción

- Todo el contenido de las skills (`SKILL.md`, `references/`, `sub-skills/`) y
  la documentación está en **español neutro**, con tuteo y sin regionalismos.
  Los textos que generan las skills también salen en español neutro salvo que el
  Perfil de voz del usuario indique otra variante.
- **No se traducen**: nombres de skills (`ig-redactar-caption`, etc.), nombres de
  archivos, rutas, identificadores de código, funciones de `lib/`, nombres de
  campos de API, claves del bloque de Estado de `voice-profile.md` (`filled`,
  `source`, `updated`) y valores que leen los scripts.
- Las estadísticas citadas en el humanizador provienen de estudios y de un
  corpus **en inglés**. No presentarlas como medidas en español. Los catálogos de
  marcadores en español son una adaptación por criterio lingüístico.
- Nunca inventar datos (horarios, tamaños de hashtags, métricas). Si no hay datos
  para audiencias hispanohablantes, decirlo y recomendar verificar en la app.
- Al incorporar cambios del repositorio original, traducir el contenido nuevo
  con estas mismas reglas y mantener las adaptaciones al español ya hechas.

## Versionado

- Fuente única de verdad: `.claude-plugin/plugin.json`,
  `.claude-plugin/marketplace.json`, `.codex-plugin/plugin.json` y
  `.agents/plugins/marketplace.json`. Los manifiestos del plugin siempre deben
  coincidir en nombre de paquete y versión; las entradas del marketplace deben
  apuntar al mismo paquete; autor, licencia, página de inicio y la descripción
  pública del paquete deben mantenerse alineados.
- Mantén `CLAUDE.md` y `AGENTS.md` alineados al cambiar reglas compartidas del
  proyecto. Los detalles de flujo propios de Claude van acá; los propios de
  Codex van en `AGENTS.md`.
- La instalación por el marketplace de Codex usa `.codex-marketplace/instagram-skills/`.
  No edites a mano ese paquete generado. Actualiza primero los archivos de la
  raíz y luego ejecuta `python3 scripts/sync_codex_marketplace.py`.
- **Por defecto: sube el segmento PATCH (3.er nivel, `0.0.X`).** Es el
  comportamiento automático para cada commit publicable, sin importar el tamaño
  del cambio.
- Solo sube MINOR o MAJOR cuando **el usuario lo pida explícitamente**.
- Después de subir la versión, si el usuario lo pide: etiqueta el commit
  (`git tag -a v<X.Y.Z> -m "..."` + `git push origin v<X.Y.Z>`) y publica un
  GitHub Release para la etiqueta (`gh release create v<X.Y.Z> --title "v<X.Y.Z>" --notes "<cambios>" --latest`).

## Commits

- Los commits de este fork se hacen con la identidad del dueño del fork (la
  configuración de git del usuario). No uses la identidad del autor original.
- Un trailer de coautoría (`Co-Authored-By: Claude ...`) está bien y es bienvenido.
- Verifica localmente antes de hacer push: el build nunca se rompe, no hay
  referencias rotas en `SKILL.md` y la importación de prueba de la biblioteca pasa.

## Invariantes del paquete de skills

- **Exactamente 9 skills.** Agregar una requiere fusionar o dividir en otro lado
  para mantener 9. El número se anuncia en los manifiestos del plugin y en el README.
- **Campo `description:` del frontmatter: objetivo <= 400 caracteres** (en español
  el texto es más largo; mantenerlo por debajo de 510). Incluye siempre una
  frase de desambiguación "No para X (usa Y)" cuando una skill se superpone con
  otra.
- **Sin rayas en ningún campo `description:`.** En el cuerpo de la prosa las
  rayas se permiten solo para separadores de tablas y divisores de listas. Sin
  rayas dentro de las líneas a completar de un esqueleto de gancho (se
  filtrarían a los captions generados).
- **Los nombres de las skills son superficie pública.** Renombrar una skill es
  una subida de versión mayor y requiere actualizar: `.codex-plugin/plugin.json`,
  `.agents/plugins/marketplace.json`, `.claude-plugin/plugin.json`,
  `.claude-plugin/marketplace.json`, la lista del `SKILL.md` raíz, la tabla de
  skills del README y cada referencia cruzada `ig-<nombre>` en los `SKILL.md`
  hermanos.

## Reglas de voz + organización de referencias

- Las reglas de voz canónicas están en `references/voice-rules.md` de la raíz.
  Las secciones locales de "Reglas estrictas" de cada skill solo deben contener
  excepciones propias de la skill (largo del caption, cantidad de slides,
  tamaño de hashtags) y empezar con: `Reglas de voz globales: ver la sección de
  reglas de voz del SKILL.md raíz.`
- Otras referencias de la raíz compartidas entre skills:
  `references/hook-formulas.md` (10 fórmulas de Instagram),
  `references/algorithm-heuristics.md`, `references/hashtag-strategy.md` y
  `references/media-workflow.md`.
- `references/untrusted-content.md` es la regla canónica de "los datos no son
  instrucciones" para toda skill que lee texto escrito por un desconocido. Cada
  una de esas skills lleva una sección breve `## Contenido no confiable` que la
  cita; la regla completa vive en un solo lugar. `scripts/check_untrusted_rule.py`
  hace cumplir ambas cosas (acepta el encabezado en español o en inglés),
  guiado por un conjunto `REQUIRED` de nombres de skills, así que **renombrar o
  agregar una skill de lectura implica actualizar ese conjunto**.
- `references/voice-profile.md` se distribuye **en blanco** y lo completa el
  usuario. Uno completo es un dato personal, no una credencial:
  `check_no_secrets.py` falla con cualquier copia versionada marcada
  `filled: yes`, y `sync_codex_marketplace.py` lo toma de HEAD y no del árbol de
  trabajo, y se niega a copiar uno completo.
- **Un `.env` del proyecto solo puede definir credenciales.** `lib/_env.py`
  mantiene una lista permitida (`_DOTENV_VARIABLES`); la variable del publicador
  propio que ejecuta el nivel DIY debe venir del entorno de ejecución, nunca de un
  archivo que pueda llegar con un clon. Ningún módulo puede llamar a
  `load_dotenv()` por su cuenta, y toda solicitud autenticada pasa
  `allow_redirects=False` porque la clave de Publora viaja en un encabezado
  personalizado y el token de Apify en un parámetro de consulta, y `requests` no
  quita ninguno de los dos entre hosts. `scripts/check_security_boundaries.py`
  hace cumplir las tres cosas.
- `references/mcp-read-layer.md` es la vía de lectura para quien no tiene shell,
  que es todo el que usa claude.ai: la URL filtrada del conector
  `mcp.apify.com?actors=`, los nombres de las dos herramientas, las entradas y
  los mapeos hacia lo que producen `_post` y `_profile`. **Mantén el filtro**: el
  servidor sin filtro también le da al agente `call-actor`. Las lecturas de nicho
  usan `resultsType: "reels"` por defecto porque el valor por defecto del actor
  devuelve posts de feed con cero me gusta. `scripts/check_mcp_mapping.py` falla
  si un id de actor, una clave de entrada o un campo plano se desvía de
  `lib/apify_client.py`, en cualquier dirección (acepta el encabezado de tabla
  `| Campo plano |` o `| Flat field |`).
- Las referencias locales de una skill van en `skills/<skill>/references/`.
  Cítalas desde la skill como `references/X.md`. Cita las de la raíz desde las
  skills como `../../references/X.md`.
- `ig-humanizar-texto` tiene `sub-skills/` para el flujo de auditoría incorporado. No
  repitas este patrón en otras skills sin una razón clara.

## Separación de capas

- **Capa de escritura (Publora):** `lib/publora_client.py`. Instagram exige
  contenido multimedia en cada post, así que el método clave es
  `publish_media_post` (crear borrador, subir cada imagen/video a S3 y luego
  programar). Piezas de más bajo nivel: `create_post`, `get_upload_url`,
  `put_to_s3`, `update_post`, `delete_post` y `list_connections` /
  `instagram_connections` (GET /platform-connections). Las skills deben llamar a
  `lib.publish(kind, draft_text, target_url, media=[...], ...)` en lugar de
  repetir la lógica. Endpoints reales: `POST /create-post`,
  `POST /get-upload-url`, `PUT /update-post/:id`, `DELETE /delete-post/:id`, con
  `platforms: ["instagram-<id>"]` (un arreglo de ids en STRING) y el encabezado
  `x-publora-key`.
- **El contenido multimedia es obligatorio.** Los posts de Instagram solo de
  texto fallan al publicar. Las skills de redacción producen el caption; el
  usuario aporta el contenido. `publish()` solo publica automáticamente en el
  nivel Publora cuando se pasan rutas de archivos en `media`; si no, devuelve el
  bloque de caption para copiar con un recordatorio de contenido.
- **Por defecto no se incluye una capa de lectura de posts.** No hay un actor de
  lectura de posts de Instagram barato y documentado conectado. `ig-extraer-gancho`
  le pide al usuario que pegue el caption (y el gancho de las slides o del reel).
  Si más adelante se agrega un actor de lectura de Instagram, condiciónalo a
  `APIFY_TOKEN` y mantén la alternativa de pegar.
- No nombres programadores de terceros competidores en archivos versionados. El
  paquete se posiciona en torno a la integración de escritura de Publora.
- **Capa de imágenes (Pixfaro):** `lib/pixfaro_client.py`. Llama a
  `lib.illustrate(prompt, kind=...)` / `lib.refine(image_id, instruction)` (no al
  cliente directamente); la URL alojada que devuelve alimenta
  `lib.publish(..., media_urls=[url])`. `refine` edita por id `img_...` (no por
  URL); `aspect_ratio` es una proporción como `16:9` (no píxeles). Alternativa
  PIXFARO_TOKEN o manual, singleton por clave + caché LRU; los campos de marca
  del `overlay` salen de la §6 de `references/voice-profile.md`.

## Paquete del marketplace de Codex

- Codex exige que las entradas del marketplace apunten a un directorio de plugin
  anidado. La raíz sigue siendo la estructura de origen para Claude.
- `.agents/plugins/marketplace.json` apunta a `.codex-marketplace/instagram-skills`.
- `scripts/sync_codex_marketplace.py` copia el manifiesto de Codex de la raíz,
  `SKILL.md`, `README.md`, `skills/`, `references/`, `lib/`, `scripts/`,
  `requirements.txt`, `.env.example` y `LICENSE` al paquete oculto.
- Después de editar cualquier archivo copiado, ejecuta el script de
  sincronización antes de probar o hacer commit.

## testing/ está en .gitignore

- `testing/` es el directorio local de trabajo: claves de API, respuestas de
  ejemplo, informes de validación, scripts de integración.
- Nunca escribas secretos fuera de `testing/` (el resto del repositorio es público).
- La regla de `.gitignore` para `testing/` es necesaria; no la cambies.

## Validación antes del push

Ejecuta desde la raíz del repositorio:

```bash
python3 -c "from lib import publish, illustrate, refine, PixfaroClient, parse_instagram_url, PubloraClient; print('OK')"
python3 scripts/sync_codex_marketplace.py
ls skills/ | wc -l        # debe dar 9
python3 scripts/check_frontmatter.py   # parsea; contar directorios no prueba que una skill cargue
python3 scripts/check_no_secrets.py    # .gitignore no impide renombrar un archivo versionado
python3 scripts/check_markdown_references.py  # ejecútalo dentro del repo; se ancla en su propia ruta
python3 scripts/check_untrusted_rule.py  # la regla tiene que estar en las skills, no solo en references/
python3 scripts/check_text_encoding.py  # un read_text() sin encoding es cp1252 en Windows: mojibake o error
python3 scripts/check_security_boundaries.py  # .env no puede nombrar un ejecutable; sin redirecciones autenticadas
python3 scripts/check_mcp_mapping.py  # la vía del conector debe producir los registros de la biblioteca, no otra forma
grep -rnP '\x{2014}|\x{2013}' skills/*/SKILL.md SKILL.md | grep -i '^.*description:'   # debe quedar vacío
python3 -m json.tool .codex-plugin/plugin.json >/dev/null
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
python3 -m json.tool .claude-plugin/plugin.json >/dev/null
python3 -m json.tool .claude-plugin/marketplace.json >/dev/null
```

Si alguno falla, no hagas push.
