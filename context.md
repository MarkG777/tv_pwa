# P3.1 - Configuracion PWA + Primer Despliegue TV
## Clima Smart TV - Contexto y Checklist

---

## Informacion del Proyecto

| Campo | Valor |
|-------|-------|
| **Practica** | P3.1 - Configuracion PWA + Primer Despliegue TV |
| **Unidad** | U3 - Pantallas Inteligentes |
| **Puntos** | 100 pts |
| **Duracion** | 4-5 hrs |
| **Herramientas** | VS Code + Chrome DevTools + ffmpeg |
| **Resolucion objetivo** | 1920x1080 (Smart TV) |
| **Proyecto** | clima-smart-tv |
| **Ruta** | `practicas/p3.1/clima-smart-tv/` |

---

## Relacion con practicas anteriores

| Practica | Aporte a P3.1 | Estado |
|----------|---------------|--------|
| P2.3 - Weather model | Modelo de datos Weather reutilizado | [ ] |
| P2.5 - API OpenWeatherMap | Misma API key (.env) y endpoints | [ ] |
| P2.6 - BLE Monitor actividad | Datos del wearable llegaran en P3.3 | [ ] |
| P1.3 - Mockup TV Figma | UI debe coincidir con mockup 1920x1080 | [ ] |

---

## Estructura del Proyecto

```
clima-smart-tv/
├── index.html              [x] Creado
├── manifest.json           [x] Creado
├── sw.js                   [x] Creado
├── .env                    [x] Creado (NO en Git)
├── .gitignore              [x] Creado
├── css/
│   └── styles.css          [x] Creado
├── js/
│   ├── app.js              [x] Creado
│   ├── config.js           [x] Creado (API key, NO en Git)
│   ├── weather.js          [x] Creado
│   └── navigation.js       [x] Creado
├── assets/
│   ├── videos/             [x] Videos creados con ffmpeg (clear, cloudy, rain, thunder .mp4)
│   └── posters/            [x] Posters creados (clear, cloudy, rain, thunder .jpg)
└── icons/
    ├── icon-192.png        [x] Creado (placeholder dorado sobre azul)
    └── icon-512.png        [x] Creado (placeholder dorado sobre azul)
```

---

## Checklist de Verificacion

### 1. Estructura y Git (15 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 1 | Estructura de carpetas correcta (js/, css/, assets/, icons/) | [x] | |
| 2 | .gitignore incluye .env antes del primer commit | [x] | |
| 3 | .gitignore incluye *.jks, *.keystore, node_modules/ | [x] | |
| 4 | API key NO aparece en ningun archivo versionado | [x] | config.js en .gitignore, .env en .gitignore |
| 5 | Primer commit realizado | [ ] | `git commit -m 'P3.1: Estructura inicial PWA clima-smart-tv'` |

### 2. manifest.json (15 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 6 | Campo `name` presente | [x] | "Clima Smart TV" |
| 7 | Campo `short_name` presente | [x] | "Clima TV" |
| 8 | Campo `display: fullscreen` | [x] | |
| 9 | Campo `orientation: landscape` | [x] | |
| 10 | Iconos 192x192 y 512x512 declarados | [x] | |
| 11 | Iconos `purpose: any maskable` | [x] | |
| 12 | `theme_color` y `background_color` definidos | [x] | |
| 13 | Screenshot con `form_factor: wide` | [x] | |

### 3. Service Worker (20 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 14 | sw.js registrado en app.js | [x] | |
| 15 | Evento `install` cachea estaticos | [x] | |
| 16 | Evento `activate` limpia caches viejos | [x] | |
| 17 | Estrategia Cache First para estaticos | [x] | |
| 18 | Estrategia Cache First para videos | [x] | |
| 19 | Estrategia Network First para API | [x] | |
| 20 | SW en estado Active en DevTools | [x] | Verificado en Aplicacion > Service Workers (sw.js registrado) |

### 4. Modo Offline (10 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 21 | App carga desde cache con Offline activado | [x] | Verificado: 0 B transferido, app carga con datos en modo Offline |
| 22 | Cache estatico poblado en DevTools | [x] | clima-tv-static-v1 y clima-tv-dynamic-v1 poblados |

### 5. Layout 1920x1080 (15 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 23 | Sin scroll, overflow hidden | [x] | |
| 24 | Safe zone activa (5% = 54px v, 96px h) | [x] | |
| 25 | Grid 2x2 ocupando el espacio | [x] | |
| 26 | Ningun elemento toca el borde | [ ] | Verificar en emulador |
| 27 | Emulador Smart TV 1080p configurado en Chrome | [ ] | Device: 1920x1080, DPR 1 |

### 6. Datos API reales (15 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 28 | API key configurada | [x] | En .env y js/config.js (gitignored) |
| 29 | 4 ciudades con datos reales | [x] | API responde 200, probado en emulador |
| 30 | Temperatura, condicion, humedad y viento mostrados | [x] | Estructura lista |
| 31 | Refresco automatico cada 10 min | [x] | |
| 32 | Manejo de errores (ciudad no encontrada, API invalida) | [x] | |

### 7. Video de Fondo (10 pts)

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 33 | Video cambia segun condicion climatica | [x] | Logica en app.js |
| 34 | Fallback a poster si video falla | [x] | |
| 35 | Al menos 2 videos (clear.mp4, rain.mp4) | [x] | 4 videos: clear, cloudy, rain, thunder .mp4 |
| 36 | Posters .jpg generados | [x] | clear, cloudy, rain, thunder creados con Python/PIL |

### 8. Navegacion D-pad

| # | Criterio | Hecho | Notas |
|---|----------|-------|-------|
| 37 | Flechas cambian foco entre tarjetas | [x] | |
| 38 | Borde dorado en tarjeta con foco | [x] | .focused con --color-focus |
| 39 | Enter selecciona ciudad y cambia video | [x] | Evento card-select |
| 40 | Navegacion 2x2 (arriba/abajo/izq/der) | [x] | NAV_MAP definido |

---

## Configuracion de Emulacion TV en Chrome DevTools

| Campo | Valor |
|-------|-------|
| Device name | Smart TV 1080p |
| Width | 1920 |
| Height | 1080 |
| Device pixel ratio | 1 |
| User agent string | Mozilla/5.0 (SMART-TV; Linux; Tizen 6.0) AppleWebKit/538.1 |

---

## Comandos Utiles

```bash
# Inicializar Git
cd clima-smart-tv
git init
git add .
git status                    # Verificar que .env NO aparece
git commit -m 'P3.1: PWA clima-smart-tv configuracion inicial'

# Convertir video con ffmpeg
ffmpeg -i tu_video.mp4 -vcodec libx264 -crf 23 -preset slow -vf scale=1920:1080 -r 30 -an -movflags +faststart clear.mp4

# Generar poster desde video
ffmpeg -i assets/videos/clear.mp4 -vframes 1 -q:v 2 assets/posters/clear.jpg

# Verificar que la API key no esta en Git
git log -S 'API_KEY'
git log -S 'tu_api_key_real'
```

---

## Rubrica de Evaluacion

| Criterio | Descripcion | Puntos | Estado |
|----------|-------------|--------|--------|
| Estructura y Git | Estructura correcta, .gitignore antes del commit, sin API key en repo | 15 | [ ] |
| manifest.json | Todos los campos requeridos, iconos 192 y 512, display fullscreen | 15 | [ ] |
| Service Worker | Registrado y activo, estrategias Cache First / Network First correctas | 20 | [ ] |
| Modo offline | App carga desde cache con Offline activado en DevTools | 10 | [ ] |
| Layout 1920x1080 | Sin scroll, safe zone activa, grid 2x2 ocupando el espacio | 15 | [ ] |
| Datos API reales | 4 ciudades con temperatura, condicion, humedad y viento | 15 | [ ] |
| Video de fondo | Cambia segun condicion climatica, con fallback a poster si falla | 10 | [ ] |
| **TOTAL** | | **100** | |

---

## Pendientes

- [x] API key configurada en `.env` y `js/config.js` (reutilizada de P2.5)
- [x] Iconos `icon-192.png` y `icon-512.png` generados
- [x] Videos creados: `clear.mp4`, `cloudy.mp4`, `rain.mp4`, `thunder.mp4`
- [x] Posters generados: `clear.jpg`, `cloudy.jpg`, `rain.jpg`, `thunder.jpg`
- [x] PWA probada en emulador Medium Phone API 36.1
- [ ] Configurar emulador Smart TV 1080p en Chrome DevTools (1920x1080)
- [ ] Verificar Service Worker activo en DevTools
- [ ] Probar modo offline
- [ ] Hacer primer commit (verificar que .env y config.js no se suben)
- [ ] Tomar capturas de evidencia
