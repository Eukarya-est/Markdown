# Docker: Stopping and Removing Containers, Networks, and Volumes for a Specific Project



To stop and remove the containers, networks, and anonymous volumes created by a specific `docker-compose.yml` file, navigate to the directory containing the `docker-compose.yml` file and execute:  

Code

```
docker compose down
```

To also remove named volumes and images (both service images and images referenced by the services), add flags:



Code

```
docker compose down --volumes --rmi all
```

- `--volumes`: Removes named volumes declared in the `volumes` section of the `docker-compose.yml` file.

 

`--rmi all`: Removes images used by the services in the `docker-compose.yml` file.



-  Pruning Unused Docker Objects (System-wide):   

To remove all unused Docker objects (stopped containers, dangling images,  unused networks, and optionally unused volumes), use the `docker system prune` command:

Code

```
docker system prune
```

To also remove all unused images (not just dangling ones), add the `-a` flag:

Code

```
docker system prune -a
```

- Removing Build Cache:

To clear the Docker build cache, which can accumulate over time, use the `docker buildx prune` command:   

Code

```
docker buildx prune
```

If using a specific builder, specify it with the `--builder` flag:

Code

```
docker buildx prune --builder <builder_name>
```

- Removing Specific Volumes:   

To remove a specific named volume not associated with a running container, first list volumes to identify the target:

Code

```
docker volume ls
```

Then, remove the desired volume:

Code

```
docker volume rm <volume_name>
```

Caution: Exercise caution when using prune commands as they can remove data. 

Always ensure you are not deleting essential data before executing these commands, especially `docker system prune -a` and `docker volume prune`.