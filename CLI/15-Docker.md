# Docker

## Steps

1. Create Dockerfile
2. Build Docker Image
3. Run Docker Container from an Image

## Create Dockerfile

``` Dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

## Build Docker Image

```cli
docker build -t [IMAGE_NAME] .
```

- -t - tag

### View Docker Images

```cli
docker images
```


## Run Docker Container

```cli
docker run -d -p [localhost_port]:[app_port] [IMAGE_NAME]
```

### View Running Containers

```cli
docker ps
```

### List files in container

```cli
docker exec [IMAGE_NAME] ls
```