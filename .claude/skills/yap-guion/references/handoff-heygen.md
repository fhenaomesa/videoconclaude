# Traspaso a heygen-video

Cuando el guion se va a producir con un avatar de HeyGen, hay una fricción concreta que
resolver y varias decisiones que conviene tomar aquí y no allí.

## El problema: el Video Agent reformula

`heygen-video` pasa el guion al Video Agent con una directiva explícita de que el texto es
*"un concepto y un tema a transmitir, no una transcripción literal"*, con libertad creativa
para expandir y rellenar la duración. Esa directiva existe por una buena razón: sin ella el
Video Agent rellena con silencios para cuadrar la duración.

El efecto secundario es que **puede reescribir el gancho**. En un vídeo corporativo da
igual. En un yap video el gancho exacto, palabra por palabra, es el producto: 14 palabras
elegidas para abrir un bucle concreto.

## La solución: bloque de texto literal

`heygen-video` tiene una salida prevista para esto. Todo elemento que deba aparecer
literalmente —cifras, citas, handles, URLs, CTAs y, en nuestro caso, **el gancho**— se
extrae a un bloque `CRITICAL ON-SCREEN TEXT` dentro del prompt. Sin ese bloque, el Video
Agent resume o parafrasea.

Al pasar el guion, incluye siempre:

```
CRITICAL ON-SCREEN TEXT:
- Opening line, verbatim, first 3 seconds: "<el gancho exacto>"
- Frame 0 overlay: "<texto del frame 0>"
- Closing line, verbatim: "<la frase de cierre que enlaza el loop>"
```

El bloque va en inglés aunque el guion esté en español: es una directiva técnica para el
Video Agent, no contenido para el espectador. La misma separación aplica al resto de
directivas (estilo, movimiento, correcciones de encuadre).

## Parámetros que hay que fijar al pasar

| Decisión | Valor para vídeo corto vertical | Por qué |
|---|---|---|
| Orientación | `portrait` | TikTok, Reels y Shorts |
| Enfoque de prompt | **Natural Flow** (guion + tono + duración, sin etiquetas de escena) | Es lo que corresponde a ≤60 s conversacional; el desglose por escenas es para >60 s o contenido con mucho dato |
| Duración | Declararla explícitamente en el prompt | El Video Agent la usa para pautar el ritmo |
| Tono | Palabras concretas: "confident and conversational", "energetic, like a tech YouTuber" | "Profesional" no dice nada |
| Presentador | Si hay `avatar_id`, referirse a él como "the selected presenter" y **no describir su aspecto** | La descripción física entra en conflicto con el avatar y degrada el resultado |

Frame Check se ejecuta solo cuando hay `avatar_id`: corrige la relación de aspecto
añadiendo notas al prompt, sin generar imágenes.

## Lo que hay que avisar antes de generar

- **Ritmo.** El guion pide cambio visual cada 1,5–2 s. El Video Agent pauta por su cuenta;
  si el resultado sale con el avatar demasiado tiempo en plano fijo, la corrección es
  reforzar las indicaciones visuales del prompt, no alargar el guion.
- **Etiqueta de IA.** El vídeo resultante es contenido generado con IA: la etiqueta es
  obligatoria en TikTok e Instagram, no penaliza el alcance y ocultarla sí lo penaliza.
- **Dry run.** `heygen-video` admite modo de previsualización sin llamar a la API. Para el
  primer vídeo de una serie compensa: se ve el prompt construido antes de gastar créditos.

## Cuándo NO encadenar

Si el gancho es de la familia **confesión**, **meta-transparencia** o cualquiera que apele
a experiencia vivida, conviene que esos tres segundos los grabe una persona real y que el
avatar sostenga sólo la parte informativa. La señal de autenticidad pesa justo donde más
se decide la retención, y es barata de conseguir: son tres segundos de móvil.
