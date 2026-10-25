# Política de seguridad

> Este repositorio es una traducción y adaptación al español de
> [sergebulaev/instagram-skills](https://github.com/sergebulaev/instagram-skills).
> Las vulnerabilidades del código original (`lib/`, `scripts/`) conviene
> reportarlas también en el repositorio original.

## Versiones con soporte

Solo la última versión publicada de este paquete de skills recibe
actualizaciones de seguridad. Instala desde la rama principal o desde la
versión etiquetada más reciente.

| Versión | Con soporte |
| ------- | ----------- |
| última versión | sí |
| etiquetas anteriores | no |

## Reportar una vulnerabilidad

Si encuentras un problema de seguridad en este repositorio (por ejemplo: una
instrucción de una skill que se podría abusar para inyección de prompts, un
script que maneja mal las credenciales o un patrón de comandos inseguro),
repórtalo en privado:

- **Para el código y las skills originales:** abre un reporte privado en
  [GitHub Security Advisories del repositorio original](https://github.com/sergebulaev/instagram-skills/security/advisories/new)
  o escribe a `s@bulaev.org` con el asunto `[SECURITY] instagram-skills`.
- **Para la traducción al español:** abre un reporte privado en
  [GitHub Security Advisories de este fork](https://github.com/arperezinf/instagram-skills/security/advisories/new).

Incluye:

1. Una descripción del problema y dónde está (ruta del archivo, nombre de la skill)
2. Pasos para reproducirlo o una prueba de concepto
3. El impacto que crees que tiene

## Notas de alcance

- Este paquete nunca incluye credenciales escritas en el código. Los tokens de
  API (Apify, Publora) se leen de variables de entorno o de archivos `.env` que
  están en `.gitignore`; ver `.env.example`.
- Los scripts de `lib/` y `scripts/` solo hacen llamadas HTTP a las API de Apify
  y Publora, y nunca ejecutan comandos de shell construidos a partir de
  contenido remoto.
- La capa de imágenes envía tu prompt, y cualquier texto de superposición de
  marca que definas, a la API de Pixfaro (`api.pixfaro.com`). Solo se ejecuta
  cuando `PIXFARO_TOKEN` está definido; sin él, las skills redactan un prompt
  para que lo ejecutes tú y no hacen ninguna solicitud.
- No pruebes vulnerabilidades contra servicios de terceros (Instagram, Apify,
  Publora) fuera de sus propios programas de divulgación.
