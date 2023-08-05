# nginx

https://hub.docker.com/_/nginx/
https://hub.docker.com/layers/library/nginx/1.25.1-alpine3.17-slim/images/sha256-3b29f9ec76a085552a6ad469b84711642b2421c7c44d2b765ca8d9e8fb25c4e8?context=explore

## build

```bash
docker build -t docker-base-image-nginx .
```

## run

https://serverfault.com/a/1022249/215599

```
envsubstr is handled automatically by the nginx image now.
```

```bash
docker run -it docker-base-image-nginx ash
```

```bash
mkdir -p /tmp/docker-base-image-nginx && \
sudo chown -R 101 /tmp/docker-base-image-nginx && \
docker run \
  -p 9999:80 \
  --name nginx \
  --rm \
  -e somekey=index2.html \
  -v /tmp/docker-base-image-nginx/cache:/var/cache/nginx \
  -v /tmp/docker-base-image-nginx/run:/var/run/nginx \
  -v /tmp/docker-base-image-nginx/conf.d:/etc/nginx/conf.d \
  -v ${PWD}/html:/usr/share/nginx/html \
  -v ${PWD}/templates:/etc/nginx/templates \
  -v ${PWD}/nginx.conf:/etc/nginx/nginx.conf:ro \
  -d docker-base-image-nginx
```

## test

```bash
docker exec -it nginx ash
```

```bash
curl http://localhost:9999
```

## stop

```bash
docker stop nginx
```
