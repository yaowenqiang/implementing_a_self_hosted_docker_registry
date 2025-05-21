# implementing a self-hosted docker registry

> docker run -it --rm -p 5000:5000 --restart always --name registry registry

> docker run -it --rm -p 5000:5000 --name registry registry

> http://localhost:5000/v2/_catalog

> Docker Registry HTTP API V2

> docker tag redis localhost:5003/redis:7.0.11-alpine

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
  -e ENV_DOCKER_REGISTRY_HOST=localhost \
  -e ENV_DOCKER_REGISTRY_PORT=5003 \
  -p 8080:80 \
  konradkleine/docker-registry-frontend:v2
```

## named volume

> cat ~/.docker/config.json

> "psFormat": "table {{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Names}}"

> docker volume ls

> alias dcpsm='docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Image}}\t{{.Mounts}}"'


```
docker run \
  -d \
  -e ENV_DOCKER_REGISTRY_HOST=localhost \
  -e ENV_DOCKER_REGISTRY_PORT=5003 \
  -p 8080:80 \
  konradkleine/docker-registry-frontend:v2
  -v registry-data:/var/lib/registry 
```

## Self-hosting registry

### Registry Mirroring with a Pull-through Cache

## Automating Builds with Notifications

> git@github.com:g0t4/docker-mongo-sample-datasets.git -b docker-registry

