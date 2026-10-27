<p align="center">
  <img src="assets/hero.png" alt="Skills de marketing para Instagram para Claude Code y Codex, código abierto con licencia MIT" width="900" />
</p>

# Skills de marketing para Instagram en español (Claude Code y Codex)

<p align="center">
  <img src="https://img.shields.io/badge/Idioma-Español-C2410C" alt="Español">
  <img src="https://img.shields.io/badge/Claude_Code-Compatible-D97757?logo=anthropic&logoColor=white" alt="Compatible con Claude Code">
  <img src="https://img.shields.io/badge/Codex-Compatible-111827" alt="Compatible con Codex">
  <img src="https://img.shields.io/badge/Claude-Skills-8A63D2" alt="Claude Skills">
  <img src="https://img.shields.io/badge/License-MIT-22C55E.svg" alt="Licencia MIT">
</p>

> **Traducción y adaptación al español** de
> [sergebulaev/instagram-skills](https://github.com/sergebulaev/instagram-skills)
> (licencia MIT), parte de la familia
> [linkedin-skills](https://github.com/sergebulaev/linkedin-skills). Las skills
> escriben en **español neutro** y el humanizador está adaptado a los indicios de
> IA propios del español.

**9 skills que convierten a Claude Code y Codex en tu equipo de contenido para
Instagram.** Escriben captions y ganchos de reels con tu voz, dimensionan
hashtags, planifican carruseles y una semana completa de contenido, leen tu
nicho con datos reales y optimizan tu perfil. A cada borrador se le quitan los
indicios de IA y espera tu aprobación antes de publicar nada. Tú aportas la
imagen o el video; las skills escriben las palabras. No hace falta programar.

Una vez instaladas, pídele a Claude Code o Codex cosas como:

- "Escribe un caption para este reel sobre [tema]"
- "Planifica una semana de posts de Instagram para mi [nicho]"
- "¿Qué está funcionando en mi nicho ahora?" (lee datos reales vía Apify)
- "Reescribe este caption para que no suene a IA"

La skill correcta se activa sola. Después revisas y apruebas.

## Qué cambia respecto del original

- Todas las instrucciones, referencias, ejemplos y mensajes de la biblioteca
  están en español.
- Las skills generan contenido en **español neutro** (tuteo, sin
  regionalismos). Puedes indicar otra variante (rioplatense, de España,
  mexicana) o tratamiento (vos, usted) en `references/voice-profile.md`.
- El **humanizador** usa catálogos de indicios de IA del español: vocabulario
  inflado (potenciar, fundamental, cabe destacar), gerundios encadenados,
  cadenas de nominalizaciones, calcos del inglés (mayúsculas en cada palabra de
  un título, "aplicar a", "hacer sentido"), la raya usada a la inglesa y signos
  de apertura ausentes.
- La estrategia de hashtags prioriza etiquetas en español y advierte sobre las
  variantes con y sin tilde o eñe.
- Las estadísticas de la versión original provienen de estudios y de un corpus
  **en inglés**; se citan como tales y no se presentan como medidas en español.
  Donde no hay datos para audiencias hispanohablantes (por ejemplo, horarios),
  las skills lo dicen y recomiendan usar las estadísticas de tu cuenta.
- Los nombres de las skills (`ig-redactar-caption`, etc.), la biblioteca `lib/` y
  la integración con Publora, Apify y Pixfaro no cambian.

## Instalación

### Claude Code (CLI / VS Code / JetBrains / app de escritorio)

Dentro de una sesión de Claude Code:

```
/plugin marketplace add arperezinf/instagram-skills#es
/plugin install instagram-skills@instagram-skills
```

El `#es` fija la rama `es`, donde está la versión en español. Si esta versión
ya está en la rama `main` de tu fork, puedes omitirlo.

Desde la terminal, sin abrir una sesión:

```bash
claude plugin marketplace add arperezinf/instagram-skills#es
claude plugin install instagram-skills@instagram-skills
```

> Si antes instalaste la versión original en inglés, el marketplace también se
> llama `instagram-skills`. Quítalo primero con
> `/plugin marketplace remove instagram-skills` para evitar el conflicto.

Para verificar: escribe `/` en una sesión y busca las skills bajo
`instagram-skills:`, o ejecuta `claude plugin list` en la terminal.

O clona el repositorio y ábrelo como directorio de trabajo:

```bash
git clone -b es https://github.com/arperezinf/instagram-skills.git
cd instagram-skills
```

### Codex CLI

> Los comandos de Codex y de `npx skills` instalan desde la rama principal del
> repositorio. Para obtener la versión en español por esa vía, la rama `es`
> tiene que estar fusionada en `main`; si no, usa un clon local de la rama `es`.

```bash
codex plugin marketplace add arperezinf/instagram-skills
codex plugin add instagram-skills@instagram-skills
```

Para probar un clon local:

```bash
git clone -b es https://github.com/arperezinf/instagram-skills.git
cd instagram-skills
codex plugin marketplace add .
codex plugin add instagram-skills@instagram-skills
```

### Cualquier agente (CLI de skills)

Un comando que funciona en Claude Code, Codex, Cursor y cualquier otro agente
que lea archivos SKILL.md:

```bash
npx skills add arperezinf/instagram-skills
```

### OpenClaw / Hermes Agent / Cursor

Clona el repositorio (rama `es`) en el directorio de skills de tu agente e
indícale en su prompt de sistema:

```
Tienes skills de marketing para Instagram en ./instagram-skills/.
Para cualquier tarea de Instagram, lee primero el skills/*/SKILL.md correspondiente.
Usa lib/url_parser.py para analizar URLs y lib/publora_client.py para publicar.
```

## Qué puedes hacer

**Escribir un caption:**

> "Escríbeme un caption de Instagram sobre cómo bajé mi tiempo de edición de 6 horas a 47 minutos. Gancho en la primera línea."

**Planificar un carrusel:**

> "Convierte mis notas en un carrusel de 10 slides sobre errores de portafolio para diseñadores junior."

**Analizar un reel viral:**

> "¿Qué gancho usa este reel? https://www.instagram.com/reel/C9_aBcDeF/ (te pego los primeros 3 segundos)"

**Dimensionar hashtags:**

> "Dame 5 hashtags para este post, dimensionados para que mi cuenta de 2.000 seguidores pueda posicionarse."

**Revisar un borrador antes de publicar:**

> "Audita este caption buscando indicios de IA y el gancho de los primeros 125 caracteres: [pega tu texto]"

**Planificar la semana:**

> "Planifica una semana de contenido en Instagram. Estoy lanzando un curso de diseño para diseñadores junior."

Cada skill te muestra primero un borrador y espera tu OK. Nada se publica sin tu
aprobación.

## Las 9 skills

| Skill | Qué hace |
|------------------------|-----------|
| **ig-redactar-caption** (redactor de captions) | Redacta un caption con el gancho en los primeros 125 caracteres, un cuerpo fácil de leer y una sola llamada a la acción, con una fórmula de gancho 2026 elegida por objetivo: guardados, compartidos, comentarios o seguidores |
| **ig-planificar-carrusel** (planificador de carruseles) | Planifica un carrusel slide por slide (hasta 10): una slide de gancho que abre un bucle, slides de valor adelantadas y una slide final que consigue el guardado y el seguimiento |
| **ig-extraer-gancho** (extractor de ganchos) | Analiza el gancho de cualquier reel o carrusel viral. Lo asigna a una de las 10 fórmulas de Instagram y devuelve una plantilla en blanco para completar |
| **ig-elegir-hashtags** (estratega de hashtags) | Arma un set dimensionado de 3-5 hashtags (nicho / medio / amplio) en el que puedas posicionarte, ajustado al post y priorizando el español. La realidad 2026, no el muro de 30 |
| **ig-humanizar-texto** (humanizador) | Quita los indicios de IA que notan los lectores en español: vocabulario inflado por densidad, puentes de revelación, ráfagas entrecortadas, tríadas apiladas, sinceridad actuada, lluvias de emojis, calcos del inglés; limita las rayas en lugar de prohibirlas. No promete engañar a los detectores (ninguna edición lo logra de forma confiable). Incluye una auditoría previa a publicar con `--mode audit` |
| **ig-planificar-semana** (planificador de contenido) | Crea un plan semanal con una mezcla de reels / carruseles / historias, ganchos por día, horarios, una meta de guardados y compartidos y un control de equilibrio de objetivos |
| **ig-adaptar-contenido** (adaptador) | Convierte un post de LinkedIn, un blog, un guion de YouTube o un hilo de X (también en otro idioma) en un carrusel o caption nativo de Instagram: nuevo gancho antes del corte de 125 caracteres, sin restos de otra plataforma, nunca un copiar y pegar |
| **ig-optimizar-perfil** (optimizador de perfil) | Audita y reescribe el perfil completo: foto, campo NOMBRE buscable, biografía (150 caracteres), link según el objetivo, categoría, destacadas (portadas, orden, nombres), la primera cuadrícula de 9 y hasta 3 posts fijados, con tarjeta de puntuación y reescrituras antes/después |
| **ig-analizar-audiencia** (análisis de audiencia) | Lee tu nicho y tu perfil con datos reales vía Apify: escanea un hashtag para ver los posts que circulan ahora (me gusta, comentarios, autor, formato) y obtiene estadísticas de seguidores/posts/biografía de cualquier cuenta, tuya o de un competidor. Instagram oculta quién dio me gusta o comentó, así que es descubrimiento de nicho más estadísticas de perfil, no una lista de quienes interactúan |

## Todo post de Instagram requiere contenido multimedia

Instagram no permite posts solo de texto. Las skills escriben el caption, el
gancho, los hashtags y el plan de slides o de tomas. **Tú aportas la imagen o el
video.** Cuando conectas Publora e indicas tus archivos a una skill, ejecuta el
flujo de publicación por ti:

```
1. crear un borrador (sin horario programado)   -> postGroupId
2. subir cada archivo a S3                       (2-10 imágenes para un carrusel, en orden)
3. programar el post                             (status=scheduled + horario)
```

Ese orden exacto importa: programar antes de que termine la subida hace competir
al programador de Instagram con el contenido. `lib/publora_client.publish_media_post(...)`
hace los tres pasos en una llamada.

## Opcional: publicación automática con Publora

Por defecto, las skills redactan el caption para que lo publiques en la app de
Instagram con tu contenido. Si quieres que Claude Code o Codex suban tu
contenido y programen el post directamente, conecta Publora. Lleva unos 2
minutos.

[Publora](https://publora.com) es una API de publicación que maneja el flujo de
contenido de Instagram (borrador, subida, programación) en una llamada.

1. Regístrate en https://app.publora.com/signup (gratis).
2. Conecta Instagram: **Channels** -> **Add Channel** -> **Instagram** y
   autoriza. Necesitas una cuenta de **Empresa o Creador** (las personales no
   son compatibles).
3. Busca tu Platform ID en **Channels** (tiene la forma `instagram-11223344`;
   copia todo, incluido `instagram-`).
4. Crea una clave de API en **Settings** -> **API** -> **Create Key** (`sk_...`).
5. Crea un archivo `.env` en la carpeta `instagram-skills` (o copia la plantilla
   con `cp .env.example .env`):
   ```
   PUBLORA_API_KEY=sk_pega_tu_clave_aqui
   INSTAGRAM_PLATFORM_ID=instagram-pega_tu_id_aqui
   ```
6. Instala dos paquetes de Python: `pip install requests python-dotenv`
7. Pruébalo pidiéndole a Claude Code: "Programa un post de prueba en Instagram
   con Publora dentro de 24 horas con esta imagen: [ruta]. Caption: 'probando la
   conexión de la API, lo cancelo desde el panel'." Si Publora devuelve un
   `postGroupId`, está listo. Cancela el post en el panel de Publora antes del
   horario programado.

> **Nota sobre el contenido:** Instagram rechaza los posts solo de texto. Si no
> le indicas una imagen o video a la skill, devuelve el caption como bloque para
> copiar y pegar más un recordatorio de adjuntar el contenido en la app.

## Opcional: generar ilustraciones con Pixfaro

El planificador de carruseles puede generar slides y tarjetas de cita y
adjuntarlas al publicar. Sin clave, redacta el prompt de la imagen y te pide que
la generes tú, así que nada se rompe. Configuración: agrega
`PIXFARO_TOKEN=pf_live_...` a tu `.env`. El color, el logo y el usuario de marca
salen de la sección 6 de tu [Perfil de voz y marca](references/voice-profile.md).

## Opcional: leer datos reales con Apify

`ig-analizar-audiencia` lee datos reales de Instagram con dos actores de Apify,
sin iniciar sesión: lo que circula bajo un hashtag y las estadísticas públicas
de un perfil.

- **Con terminal:** agrega `APIFY_TOKEN=apify_api_...` a tu `.env`.
- **En claude.ai:** agrega el servidor MCP de Apify como conector personalizado
  con esta URL, **manteniendo el filtro** `?actors=` (sin él, el agente podría
  ejecutar cualquier actor de la Store con costo):
  ```
  https://mcp.apify.com?actors=apify/instagram-hashtag-scraper,apify/instagram-profile-scraper
  ```

Detalles y mapeo de campos: [`references/mcp-read-layer.md`](references/mcp-read-layer.md).

## Reglas de voz

Todas las skills las siguen automáticamente:

1. Español neutro con ortografía completa (tildes, ¿ ¡), sin calcos del inglés.
2. Rayas limitadas a alrededor de una cada 100 palabras. Lo que delata no es el
   carácter sino la densidad y el uso a la inglesa.
3. Nombres propios siempre con mayúscula.
4. Sin acumulaciones de vocabulario de IA. Un "fundamental" en un párrafo es
   español normal; tres marcadores en un párrafo se leen como IA y el párrafo se
   reescribe.
5. Los números concretos le ganan a los adjetivos. "47 minutos" le gana a "rápido".
6. El gancho va en los primeros 125 caracteres (todo lo demás queda detrás del
   corte de "más").
7. Los hashtags son dimensionamiento, no volumen: 3-5 etiquetas dimensionadas,
   no 30. 0-3 emojis.

## Solución de problemas

| Problema | Solución |
|--------------------------------------------------|---------|
| Las skills no se activan cuando pregunto por Instagram | Verifica que instalaste con `/plugin install` o `codex plugin add` y abre una conversación nueva. En Claude Code, ejecuta `/reload-plugins`. |
| "PUBLORA_API_KEY not set" | Falta el archivo `.env` o está en la carpeta equivocada. Debe estar en la raíz de `instagram-skills/`. |
| "401 Invalid API key" de Publora | La clave es incorrecta o fue revocada. Crea una nueva en Publora: Settings > API > Create Key. |
| "Invalid platform ID format" | Tu `INSTAGRAM_PLATFORM_ID` es incorrecto. Copia el valor completo `instagram-...` desde Channels en Publora. |
| El post falló con "media required" | Instagram no permite posts solo de texto. Indícale a la skill una imagen o un video. |
| El carrusel fue rechazado | Un carrusel tiene 2-10 elementos, todo imágenes o todo video. No se pueden mezclar. |
| La cuenta personal no se conecta | La API de Instagram necesita una cuenta de Empresa o Creador. Cámbiala en la configuración de la app y vuelve a conectar. |
| Conflicto de marketplace al instalar | Ya tienes agregado el marketplace original `instagram-skills`. Quítalo con `/plugin marketplace remove instagram-skills` y vuelve a agregar este. |
| Falla `pip install` | Usa un entorno virtual: `python -m venv venv && source venv/bin/activate && pip install requests python-dotenv` |

## Referencias compartidas

- [`references/voice-rules.md`](references/voice-rules.md) - las reglas de voz canónicas que heredan todas las skills
- [`references/hook-formulas.md`](references/hook-formulas.md) - las 10 fórmulas de gancho de Instagram con esqueletos y objetivos
- [`references/algorithm-heuristics.md`](references/algorithm-heuristics.md) - señales de ranking, horarios y límites de Instagram 2026
- [`references/hashtag-strategy.md`](references/hashtag-strategy.md) - el modelo de hashtags dimensionados 2026 (3-5, no 30)
- [`references/media-workflow.md`](references/media-workflow.md) - el flujo de borrador, subida y programación
- [`references/voice-profile.md`](references/voice-profile.md) - tu Perfil de voz y marca (variante de español incluida)

## Para desarrolladores

```
instagram-skills/
  skills/             SKILL.md con frontmatter; nativo en Claude Code y Codex, otros lo leen como markdown
  .codex-marketplace/ paquete anidado de Codex generado (ejecuta scripts/sync_codex_marketplace.py)
  lib/                Python puro, funciona en cualquier entorno de agentes
  references/         markdown puro, funciona en cualquier lado
  scripts/            CLI en Python puro, funciona en cualquier lado
```

Ejemplo rápido en Python:

```python
import sys; sys.path.insert(0, "ruta/a/instagram-skills")
from lib import parse_instagram_url, PubloraClient, publish

parsed = parse_instagram_url("https://www.instagram.com/reel/C9_aBcDeF/")
print(parsed["url_type"], parsed["shortcode"])  # reel C9_aBcDeF

client = PubloraClient()  # lee PUBLORA_API_KEY del entorno
client.publish_media_post(
    content="abajo te dejo la configuración en 3 pasos, cópiala\n\n#nicho #medio #amplio",
    platforms=["instagram-11223344"],
    media=["slide1.jpg", "slide2.jpg", "slide3.jpg"],  # rutas locales, en orden
    scheduled_time="2026-07-01T15:00:00.000Z",
)
```

Antes de hacer push, ejecuta las validaciones listadas en `CLAUDE.md`.

## Créditos y licencia

Skills originales: [sergebulaev/instagram-skills](https://github.com/sergebulaev/instagram-skills),
de [Creative Content Crafts](https://cccrafts.ai). Si te resultan útiles, una
estrella en el repositorio original ayuda a que otras personas las encuentren.

Licencia MIT (ver `LICENSE`). Publicación impulsada por [Publora](https://publora.com).

Documentación de referencia:
[API de Publora](https://docs.publora.com) ·
[Publicación de contenido en la API Graph de Instagram](https://developers.facebook.com/docs/instagram-api/guides/content-publishing) ·
[Instalar plugins en Claude Code](https://code.claude.com/docs/en/discover-plugins)
