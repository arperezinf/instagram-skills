# Sub-skill: crear / actualizar el Perfil de voz y marca

Crea o actualiza `../../../references/voice-profile.md` para que todas las
skills de redacción de este paquete escriban con la voz real del usuario y no
con una voz "humana" genérica. Funciona en cualquier agente (Claude Code, Codex,
OpenClaw): la vía principal solo necesita que el usuario pegue textos propios.
Un token de lectura (Apify) es un acelerador opcional, nunca un requisito.

## Cuándo se ejecuta

- El usuario dice "arma mi perfil de voz", "aprende mi voz" o invoca
  `ig-humanizar-texto --mode profile`.
- También ofrécelo la primera vez que una skill de redacción se ejecuta y
  encuentra `filled: no`.

## Entradas (cualquiera alcanza)

1. **Muestras pegadas (opción portátil por defecto).** Pide 3-6 posts reales de
   Instagram del usuario. Esto alcanza por sí solo; no hace falta token ni
   historial.
2. **Con la capa de lectura (opcional).** Si hay un token configurado, obtén la
   actividad reciente del usuario con la capa de lectura del paquete como
   muestras adicionales, además de las pegadas.
3. **Manual.** El usuario también puede indicar directamente su nicho, sus
   reglas y sus links.

## Pasos

1. Reúne 3 o más muestras reales de los textos del usuario.
2. Extrae la huella de voz de las muestras, no de suposiciones: ritmo de las
   oraciones, aperturas recurrentes, hábitos de puntuación, vocabulario
   preferido, palabras que evita, uso de emojis y hashtags, **variante de
   español** (neutro, rioplatense, de España, mexicano, etc.) y **forma de
   tratamiento** (tú, vos, usted, ustedes/vosotros).
3. Deduce nicho, cliente ideal y pilares a partir de los temas de las muestras;
   confírmalos en lugar de adivinar.
4. Registra las reglas estrictas y el estilo de llamada a la acción y de links
   que revelan las muestras o que indica el usuario.
5. Escribe `../../../references/voice-profile.md`: completa las secciones 1-5,
   copia textualmente las 2-4 líneas más fuertes en "Ejemplos característicos"
   y deja el bloque de Estado en `filled: yes`, `source: <pasted|read-layer|manual>`,
   `updated: <fecha de hoy>` (mantén esas claves en inglés: los scripts las leen).
6. Muestra el perfil completo para su aprobación antes de guardarlo; avísale al
   usuario que todas las skills de redacción lo respetarán automáticamente.

## Reglas estrictas

- Arma la huella a partir de las muestras REALES del usuario. Nunca inventes una voz.
- Conserva sus particularidades (una frase favorita, un ritmo inusual, sus
  regionalismos). Son el punto; la limpieza genérica de indicios de IA se aplica
  después a los borradores, no al perfil.
- Con solo 3 muestras, aclara que es una primera versión; sugiere repetirlo con
  10 o más posts.
- Nunca pongas en el archivo nada que el usuario no haya aportado.

## Relacionadas

- Las skills de redacción del paquete leen el perfil completo antes de escribir.
- Repítelo cada vez que cambie la voz o el enfoque del usuario.
