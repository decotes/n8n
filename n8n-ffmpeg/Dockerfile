FROM jrottenberg/ffmpeg:6.1-alpine AS ffmpeg

FROM docker.n8n.io/n8nio/n8n:latest

USER root

# Binarios
COPY --from=ffmpeg /bin/ffmpeg /usr/local/bin/ffmpeg
COPY --from=ffmpeg /bin/ffprobe /usr/local/bin/ffprobe

# Librerías requeridas -> rutas estándar
COPY --from=ffmpeg /lib /usr/local/lib/ffmpeg-lib
COPY --from=ffmpeg /usr/lib /usr/local/lib/ffmpeg-usr-lib

# Registrar rutas para el dynamic linker (musl)
RUN printf "%s\n" \
  "/usr/local/lib/ffmpeg-lib" \
  "/usr/local/lib/ffmpeg-usr-lib" \
  > /etc/ld-musl-x86_64.path

# (Opcional pero recomendado) también lo dejamos en ENV por si acaso
ENV LD_LIBRARY_PATH=/usr/local/lib/ffmpeg-lib:/usr/local/lib/ffmpeg-usr-lib

USER node
