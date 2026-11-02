FROM ghcr.io/openrailassociation/netzgrafik-editor-backend:2.9.1 AS nge-backend

# The published image is based on paketobuildpacks/ubuntu-noble-run-tiny (distroless-like, no shell, no package manager),
# so install the tools in a matching Ubuntu and stage them together with the shared libraries missing in the published image.
FROM ubuntu:24.04 AS tools
RUN apt-get update && apt-get -y install --no-install-recommends bash curl nginx && rm -rf /var/lib/apt/lists/*
COPY --from=nge-backend / /nge-backend
RUN set -eu; \
    mkdir -p /staging; \
    for bin in /usr/bin/bash /usr/bin/curl /usr/sbin/nginx; do \
      cp --parents "$bin" /staging; \
      for lib in $(ldd "$bin" | grep -o '/[^ ]*'); do \
        lib="$(realpath "$(dirname "$lib")")/$(basename "$lib")"; \
        [ -e "/nge-backend$lib" ] || { mkdir -p "/staging$(dirname "$lib")"; cp -L "$lib" "/staging$lib"; }; \
      done; \
    done; \
    cp -r --parents /etc/nginx /usr/share/nginx /staging; \
    # dynamic modules are not staged
    rm -f /staging/etc/nginx/modules-enabled/*; \
    mkdir -p /writable/var/log/nginx /writable/var/lib/nginx

FROM nge-backend
COPY --from=tools /staging /
# user of the published image
COPY --from=tools --chown=1002:1001 /writable /
