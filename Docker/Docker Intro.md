# Docker Intro

[toc]

## 1. URL

- docker hub	
  - https://hub.docker.com/
- docker docs
  - https://docs.docker.com/

## 2. Install with Debian

### 1) Add Docker's official GPG key:

```shell
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### 2) Add the repository to Apt sources:

```shell
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose
```

## 3. Command

- Image list

  ```shell
  docker images
  ```

- Image remove

  ```shell
  docker image rm 
  ```

- image run

  ```shell
  docker container run [OPTIONS] [IMAGE-NAME] [COMMAND] [ARG...]
  ```

  ```shell
  docker run --name [CONTAINER-NAME] IMAGE
  ```

  ```shell
  docker run -p [PORT-NUMBER] IMAGE
  ```

- container run

  ```shell
  docker start [CONTAINER-NAME]
  ```

- container status

  ```shell
  docker ps
  ```

- container stop

  ```shell
  docker stop [OPTIONS] [CONTAINER-NAME]
  ```

- container delete

  ```shell
  docker rm [OPTIONS] [CONTAINER-NAME]
  ```

  - with force

  ```shell
  docker rm --force 'NAMES'
  ```

- show logs

  ```shell
  docker logs [OPTIONS] [CONTAINER-NAME]
  ```

  - on real time

  ```shell
  docker logs -f [OPTIONS] [CONTAINER-NAME]
  ```

- container execution

  ```shell
  docker exec [option] [CONTAINER-NAME] [CONTAINER-COMMAND]
  ```

  - bash execution

  ```shell
  docker exec -it [CONTAINER-NAME] bash
  ```