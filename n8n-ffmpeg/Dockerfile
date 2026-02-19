FROM docker.n8n.io/n8nio/n8n:latest

USER root

RUN set -eux; \
  if command -v apt-get >/dev/null 2>&1; then \
    apt-get update && apt-get install -y ffmpeg && rm -rf /var/lib/apt/lists/*; \
  elif command -v apk >/dev/null 2>&1; then \
    apk add --no-cache ffmpeg; \
  elif command -v microdnf >/dev/null 2>&1; then \
    microdnf install -y ffmpeg && microdnf clean all; \
  elif command -v dnf >/dev/null 2>&1; then \
    dnf install -y ffmpeg && dnf clean all; \
  elif command -v yum >/dev/null 2>&1; then \
    yum install -y ffmpeg && yum clean all; \
  else \
    echo "No supported package manager found"; \
    exit 1; \
  fi

USER node
