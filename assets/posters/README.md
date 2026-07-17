# assets/posters/

Imagenes estaticas como fallback si el video no carga:
- clear.jpg
- cloudy.jpg
- rain.jpg
- thunder.jpg

Generar poster desde video con ffmpeg:
ffmpeg -i assets/videos/clear.mp4 -vframes 1 -q:v 2 assets/posters/clear.jpg
