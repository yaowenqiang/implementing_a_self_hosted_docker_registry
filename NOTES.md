# implementing a self-hosted docker registry

> docker network create my-network

> docker run -it --rm -p 5000:5000 --restart always --name registry --network my-network registry 

> docker run -it --rm -p 5000:5000 --name registry --network my-network registry 

> http://localhost:5000/v2/_catalog

> Docker Registry HTTP API V2

> docker tag redis localhost:5000/redis:7.0.11-alpine

[registry:port] repository [tag]

> source code 

> https://github.com/distribution/distribution/tree/main

> search for defaultDomain, defaultTag

> docker push  localhost:5003/redis:7.0.11-alpine
> docker pull  registry:5003/redis:7.0.11-alpine

## Insecure Registry

> http://localhost:5003/v2/redis/tags/list

press cmd + enter on mac or alter + ente on windows can open a new background tab with what in your address input

> docker registry UI

```
docker run \
  -d \
  -e ENV_DOCKER_REGISTRY_HOST=registry \
  -e ENV_DOCKER_REGISTRY_PORT=5000 \
  -p 8080:80 \
  --network my-network \
  konradkleine/docker-registry-frontend:v2
```

## pull images from other machine

### add insecure-registries
```
vim /etc/docker/daemon.json

  "insecure-registries": ["your-registry-ip:port"],

systemctl reload docker

docker pull your-registry-ip:port/redis

```

## named volume

> cat ~/.docker/config.json

> "psFormat": "table {{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Names}}"

> docker volume ls

> alias dcpsm='docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Image}}\t{{.Mounts}}"'


```
docker run \
  -d \
  -p 5000:5000 \
  --network my-network \
  -v registry-data:/var/lib/registry \
  registry
```

## Self-hosting registry

### Registry Mirroring with a Pull-through Cache

> REGISTRY_PROXY_REMOTEURL: https://registry-1.docker.io


## Automating Builds with Notifications

> git@github.com:g0t4/docker-mongo-sample-datasets.git -b docker-registry

> docker compose up --force-recreate vetted-registry

> https://github.com/distribution/distribution-library-image

> RequestBin

> docker compose logs --follow vetted-registry | grep --line-buffered -o '{.*}' | jq

> docker compose logs --follow vetted-registry | grep --line-buffered -o '{.*}' | jq -c '{ time, level: .level[0,4], msg }'

> docker compose logs --follow vetted-registry | grep --line-buffered -o '{.*}' | jq -c '{time: .time[0:19], level: .level[0:4], msg}'

> docker compose exec containername sh

> docker ps -q | xargs -n1 docker port
> docker compose up --force-recreate vetted-registry

> docker pull busybox
> docker tag busybox localhost:55000/busybox
> docker push localhost:55000/busybox
> docker compose up --force-recreate -V vetted-registry

## Cleaning up Images and Configuring Storage

### inmemory storage

> in-memory storage driver

> storagedriver.go 
> driver.go

```yml
environment:
    REGISTRY_STORAGE: inmemory
    REGISTRY_LOG_LEVEL: debug
```

> watch -n1 -d curl -s localhost:5000/v2_catalog

### delete

```yml
    delete: 
        enabled: true
```

> registry --help
> registry garbage-collect --dry-run


