FROM ghcr.io/schweizerischebundesbahnen/netzgrafik-editor-backend:1.0.0
# FROM ghcr.io/schweizerischebundesbahnen/netzgrafik-editor-frontend:latest@sha256:ce559308cfb991afe7ff2a8e2d2473d0aa9a5d991213a3473663f322f2039ade

# docker buildx build --platform linux/arm64 . --tag ghcr.io/schweizerischebundesbahnen/netzgrafik-editor-backend-local:arm64
# docker buildx build --platform linux/arm64 . --tag ghcr.io/schweizerischebundesbahnen/netzgrafik-editor-frontend-local:arm64

USER root
RUN apt-get update && apt-get -y install curl wget telnet net-tools nginx
RUN mkdir -p /var/log/nginx && chown -R cnb /var/log/nginx && mkdir -p /var/lib/nginx &&  chown -R cnb /var/lib/nginx
USER cnb

#CMD ["sleep", "infinity"]
# spring.flyway.locations=classpath:db/migration,filesystem:/another/migration/directory

# BOOT-INF/classes/application.yml