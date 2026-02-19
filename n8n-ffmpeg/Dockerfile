FROM jrottenberg/ffmpeg:6.1-alpine AS ffmpeg

FROM docker.n8n.io/n8nio/n8n:latest
RUN echo "=== USING N8N STAGE ==="

USER root
COPY --from=ffmpeg /bin/ffmpeg /usr/local/bin/ffmpeg
COPY --from=ffmpeg /bin/ffprobe /usr/local/bin/ffprobe
USER node
