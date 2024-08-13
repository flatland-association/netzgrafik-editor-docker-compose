FROM ghcr.io/schweizerischebundesbahnen/netzgrafik-editor-backend:2.7.5

USER root
RUN apt-get update && apt-get -y install curl wget telnet net-tools nginx
RUN mkdir -p /var/log/nginx && chown -R cnb /var/log/nginx && mkdir -p /var/lib/nginx &&  chown -R cnb /var/lib/nginx
USER cnb