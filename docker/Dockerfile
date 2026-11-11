# The documentation site (https://nebulacommander.com) as a static nginx image:
#   ghcr.io/nebula-commander/docs
#
# Built by .github/workflows/docs-image.yml with a context holding this file, default.conf,
# and Hugo's output in public/. There are no RUN steps, so the arm64 image builds without
# emulation.
FROM nginx:stable-alpine

ENV NGINX_ENTRYPOINT_QUIET_LOGS=1
COPY default.conf /etc/nginx/conf.d/default.conf
COPY public/ /usr/share/nginx/html/

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD wget -q -O /dev/null http://127.0.0.1/healthz || exit 1
