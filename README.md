# Netzgrafik-Editor Deployment

This repository provides deployment for Netzgrafik Editor (frontend, backend, DB for backend):
* a Docker Compose file for local deployment
* Helm charts for deployment on a Kubernetes cluster

It is based on the published images from the ghcr (GitHub container registry) at
[SchweizerischeBundesbahnen](https://github.com/orgs/SchweizerischeBundesbahnen/packages).
No local dev setup (`mvn`, `npm` etc.) beyond `docker` and `docker-compose` are required. 

For local dev setup, use the source repos
* [netzgrafik-editor-frontend](https://github.com/SchweizerischeBundesbahnen/netzgrafik-editor-frontend)
* [netzgrafik-editor-backend](https://github.com/SchweizerischeBundesbahnen/netzgrafik-editor-backend)


## Local Deployment with Docker Compose

Start containers:

```shell
docker-compose up -d
```

Stop containers:

```shell
docker-compose stop 
```

Remove containers and data:

```shell
docker-compose down 
```

### Overview
![Overview](./images/docker_compose.png)

Keycloak tokens are issued for `http://localhost:8081/realms/netzgrafikeditor`.
As the backend verifies these tokens, a reverse proxy needs to be installed in the

### Deployment on a Kubernetes Cluster with Helm

## License

This project is licensed under [Apache 2.0](LICENSE).
