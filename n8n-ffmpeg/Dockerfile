FROM jrottenberg/ffmpeg:6.1-alpine AS ffmpeg

FROM docker.n8n.io/n8nio/n8n:latest

USER root

# Binarios
COPY --from=ffmpeg /bin/ffmpeg /usr/local/bin/ffmpeg
COPY --from=ffmpeg /bin/ffprobe /usr/local/bin/ffprobe

# Librerías de Alpine (musl) que necesitan esos binarios
COPY --from=ffmpeg /lib /ffmpeg-libs/lib
COPY --from=ffmpeg /usr/lib /ffmpeg-libs/usr-lib

# Decirle al loader dónde encontrarlas
ENV LD_LIBRARY_PATH=/ffmpeg-libs/lib:/ffmpeg-libs/usr-lib

USER node
