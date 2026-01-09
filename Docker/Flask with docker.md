# Docker

[toc]

## 1. Build the Docker image

```shell
docker build -t [CONTAINER-NAME] .
```

## 2. Docker container

```shell
docker run -p [DOCKER-PORT-NUMBER]:[SERVER-PORT-NUMBER] [CONTAINER-NAME]
```

- -d: Run container in background and Print container ID

```shell
docker run -d -p [DOCKER-PORT-NUMBER]:[SERVER-PORT-NUMBER] [CONTAINER-NAME]
```



