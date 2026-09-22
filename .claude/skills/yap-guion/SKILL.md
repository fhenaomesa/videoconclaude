---
version: 1.0.0
name: yap-guion
description: |
  Escribe guiones de vídeo corto vertical (Instagram Reels, TikTok, YouTube Shorts) en
  formato yap / talking head: gancho de menos de 14 palabras, micro-bucles de retención,
  pago completo y cierre en loop. Entrega 5 variantes de gancho de familias distintas
  para que el creador pueda testear cuál retiene mejor.
  Úsala siempre que alguien pida un guion, un texto o una idea para un vídeo corto
  vertical, aunque no diga la palabra "guion": "hazme un reel sobre X", "un TikTok de
  esto", "un vídeo corto explicando Y", "necesito ganchos para", "un short de 30
  segundos", "qué digo en este vídeo", "script para Reels", "hook para TikTok",
  "guion para mi avatar", "texto para un vídeo de IA".
  También cuando pidan mejorar, reescribir o diagnosticar un guion o un gancho que ya
  tienen ("este reel no retiene", "mejórame este gancho", "por qué no funciona este
  vídeo"), o cuando pidan varias variantes de gancho para testear.
  Encadena con heygen-video: si además quieren generar el vídeo con un avatar, escribe
  aquí el guion y pasa el resultado a heygen-video con el gancho blindado como texto
  literal.
  NO es para: guiones de vídeo largo o YouTube horizontal, copy de posts estáticos o
  carruseles, newsletters, guiones de podcast completo, ni generar el vídeo en sí
  (eso es heygen-video).
argument-hint: "[tema] [--duracion 30] [--plataforma reels|tiktok]"
allowed-tools: Read, Write, Edit, Bash, WebSearch, mcp__heygen__*
---

## Por qué existe esta skill

Un vídeo corto no se pierde por el tema ni por la edición: se pierde en los tres primeros
segundos. Entre el 50% y el 60% de los abandonos ocurren ahí. Todo lo que sigue en esta
skill existe para ganar esa primera audición y, después, para que el espectador tenga un
motivo concreto para reenviar el vídeo a alguien — que es la señal que abre el alcance
más allá de los seguidores.

El detalle completo de la investigación que sostiene esto está en `investigacion/` en la
raíz del repositorio. Aquí sólo están las decisiones.

## Antes de escribir: sólo lo imprescindible

Pregunta **una o dos cosas como mucho**, nunca un formulario. La mayoría de las peticiones
ya traen implícita la mitad de la información ("un reel de 30 segundos explicando qué es
un avatar de IA" ya te da tema, duración y formato).

Lo que necesitas saber antes de escribir:

1. **Tema y ángulo** — de qué va y, sobre todo, qué postura se defiende.
2. **Duración objetivo** — si no la dicen, asume 30 s.
3. **A quién va dirigido** — con esto se construye el motivo de reenvío.

Lo que puedes inferir sin preguntar: plataforma (Reels salvo que digan otra cosa), tono
(el del propio usuario al pedirlo), idioma (el de la conversación).

Si falta el ángulo, no preguntes "¿qué ángulo quieres?" — propón dos y que elija. Es más
rápido para quien te lee y produce mejores guiones.

## Paso 1 — Cinco ganchos antes del guion

Este paso no se salta, y es el que hace útil a la skill. Un guion con un gancho flojo es
trabajo perdido; cinco ganchos permiten testear.

Escribe **5 ganchos de 5 familias distintas** (nunca cinco variaciones del mismo). Las
familias, con ejemplos, están en `references/ganchos.md` — léelo si necesitas inspiración
o si el tema se resiste.

Reglas que aplican a los cinco:

- **Máximo 14 palabras habladas.** Si no cabe, no es un gancho: es una introducción.
- **Cero saludo, cero "en el vídeo de hoy", cero presentación.** El primer segundo es el
  activo más caro del vídeo.
- **Promesa concreta o conflicto real.** "La IA está revolucionando el mundo" no es un
  gancho porque no promete nada ni contradice nada.
- Cada uno lleva su **texto de frame 0**, que debe entenderse en silencio y complementar
  al gancho hablado en vez de repetirlo palabra por palabra.

Preséntalos numerados, con la familia entre paréntesis, y pregunta cuál quiere — o si
prefiere que elijas tú y se lo justifiques. Así:

```
1. (Contraria)  "Tu avatar no necesita ser más realista. Necesita ser menos perfecto."
   Frame 0: NO ES POR EL REALISMO
2. (Aviso de error) ...
```

## Paso 2 — El guion, cronometrado

Escribe el guion sólo del gancho elegido. Formato de entrega: **tabla de tiempo, voz y
visual**, porque es lo único que se puede producir directamente.

| Tiempo | Voz | Visual |
|---|---|---|

La arquitectura, con sus tiempos, está en `references/estructura.md`. El esqueleto es
siempre el mismo: frame 0 → gancho → contexto de una frase → cuerpo en micro-bucles →
pago completo → CTA → loop.

Cuatro cosas que deciden si el guion funciona:

- **Un micro-bucle cada 8–12 segundos.** Una frase que abre tensión antes de resolverla
  ("y aquí es donde casi todo el mundo se equivoca"). Sin esto la atención se cae en el
  segundo 10 aunque el contenido sea bueno.
- **El pago entero antes del CTA.** Retener la respuesta a cambio de un comentario se
  nota y se castiga con scroll. El CTA va después, montado sobre la emoción del pago.
- **Un motivo explícito para guardarlo y otro para reenviarlo.** "Mándaselo al que te
  dijo que esto se nota" convierte mucho mejor que "comparte si te ha gustado", porque
  le quita al espectador las dos decisiones.
- **Los últimos tres segundos enlazan con los primeros.** El loop multiplica el tiempo
  visto sin producción extra.

**Escribe para el oído.** Frases de 10 a 18 palabras, una idea por frase, voz activa,
contracciones y muletillas. Si lo va a locutar una voz sintética esto deja de ser estilo y
pasa a ser funcional: las frases largas salen planas. Marca las respiraciones con puntos
suspensivos.

**Cálculo de duración:** en español, entre 2,5 y 3 palabras por segundo a ritmo de vídeo
corto. Un guion de 30 s son unas 75–90 palabras. Cuenta las palabras y dilo al entregar —
un guion que se pasa de largo obliga a acelerar la locución y arruina el ritmo.

## Paso 3 — Revisión honesta antes de entregar

Repasa el guion contra el checklist de 12 puntos de `references/estructura.md` y **di qué
puntos quedan flojos** en vez de afirmar que están todos cubiertos. Un guion con un motivo
de reenvío débil sigue siendo entregable, pero quien lo produce tiene que saberlo para
decidir si lo publica o lo reescribe.

Si algo no se puede cumplir por la naturaleza del tema (por ejemplo, un tema técnico sin
carga emocional difícilmente genera reenvíos), dilo y propón el ajuste que sí lo lograría.

## Entrega

Guion en la conversación siempre. Si hay más de uno, o si el usuario está produciendo en
serie, guárdalo también en `guiones/<fecha>-<tema-corto>.md` para que tenga el histórico.

Cierra indicando **qué medir**: la retención a 3 segundos es la única métrica que decide
si el gancho elegido fue el correcto. Por debajo del 50% el problema es el gancho, no el
algoritmo ni la edición. Por encima del 70%, ese gancho pasa a ser plantilla reutilizable.

## Encadenado con heygen-video

Cuando además quieran generar el vídeo con un avatar, escribe aquí el guion y luego pasa a
`heygen-video`. Hay una fricción real que hay que resolver en el traspaso: el Video Agent
de HeyGen trata el guion como *un concepto a transmitir, no una transcripción literal*, y
reformula. Para un vídeo corporativo da igual; para un yap video el gancho exacto es el
producto entero.

Cómo se blinda, paso a paso: `references/handoff-heygen.md`.

## Modo diagnóstico

Si traen un guion o un vídeo que ya existe y no funciona, no reescribas de entrada.
Diagnostica en este orden, que es el de la cadena causal — cada eslabón sólo importa si el
anterior está resuelto:

1. **¿El gancho cabe en 14 palabras y promete algo concreto?** Es el fallo en la gran
   mayoría de los casos.
2. **¿Hay intro, saludo o logo antes del gancho?**
3. **¿Hay un micro-bucle antes del segundo 12?**
4. **¿El pago llega entero, y antes del CTA?**
5. **¿Hay un motivo nombrado para reenviarlo a alguien concreto?**
6. **¿Cierra en loop?**

Nombra el primer eslabón roto, explica por qué rompe la cadena, y ofrece la corrección
concreta. Arreglar el gancho de un vídeo con un cuerpo decente rinde más que reescribirlo
entero.

## Reglas de trato

- Responde en el idioma de quien escribe; el guion va en el idioma del vídeo, que puede
  ser distinto — confírmalo sólo si hay ambigüedad real.
- No narres el proceso interno de la skill ("ahora voy a la fase 2"). Entrega ganchos,
  entrega guion.
- No inventes datos, cifras ni estudios dentro de un guion. Si el guion pide un dato y no
  lo hay, déjalo marcado como `[DATO A VERIFICAR]` en vez de rellenarlo: un dato inventado
  en un vídeo publicado es un problema de quien lo publica, no tuyo.
- Si el vídeo se va a producir con avatar o voz de IA, recuérdalo una vez: la etiqueta de
  contenido generado por IA es obligatoria en TikTok e Instagram, no penaliza el alcance,
  y ocultarlo sí lo penaliza.
