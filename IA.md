# IA.md — Uso de Inteligencia Artificial en P3.1

## Correcciones de código

- Se corrigió el `z-index` del video de fondo y overlay en `styles.css` para que el video se muestre como fondo de pantalla.
- Se ajustó el overlay de 0.50 a 0.35 para mejorar la visibilidad de los videos.
- Se añadió soporte para click del mouse en `navigation.js` además de la navegación D-pad.
- Se separaron los iconos `any` y `maskable` en `manifest.json` para eliminar warnings de Chrome.
- Se subió la versión del cache del Service Worker a `v2` para forzar el precacheo de los videos nuevos.
- Se verificó que la API key no quede expuesta en ningún archivo versionado.

## Optimización de videos

- Se descargaron videos de Pexels y Pixabay y se optimizaron con ffmpeg a 1920x1080, 10s, H.264, sin audio.
- Se generaron posters nuevos desde el primer frame de cada video.

## Verificación

- Se probó la app en Chrome con emulación Smart TV 1080p y modo offline.
- Se verificó el Service Worker, Cache Storage y manifest en DevTools.
