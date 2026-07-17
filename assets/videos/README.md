# assets/videos/

Coloca aqui los videos de fondo por condicion climatica:
- clear.mp4   (cielo despejado, azul)
- cloudy.mp4  (nublado)
- rain.mp4    (lluvia)
- thunder.mp4 (tormenta electrica)

Optimizar con ffmpeg:
ffmpeg -i tu_video.mp4 -vcodec libx264 -crf 23 -preset slow -vf scale=1920:1080 -r 30 -an -movflags +faststart clear.mp4
