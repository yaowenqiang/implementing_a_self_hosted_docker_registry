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

