# Docker

Docker runs a process in a container from an image. The daemon is `docker.service`.

```bash
$ sudo pacman -S docker docker-compose
$ sudo systemctl enable --now docker
$ sudo usermod -aG docker "$USER"
```

Group membership applies at the next login. Until then, prefix the commands with `sudo`.

```bash
$ sudo systemctl start docker
$ sudo systemctl stop docker
$ sudo systemctl restart docker
$ sudo systemctl status docker
$ docker version
$ docker info
```

## Images

```bash
$ docker pull alpine
$ docker pull alpine:3.20
$ docker images
$ docker image ls
$ docker inspect alpine
$ docker history alpine
$ docker tag alpine:3.20 <name>:<tag>
$ docker rmi alpine
$ docker rmi <image-id>
```

`pull` downloads an image. The part after `:` is the tag. With no tag, Docker uses `latest`. `images` and `image ls` are the same list. `history` is the layers. `tag` adds another name to an image that is already local. `rmi` removes an image that no container is using.

Save an image to a file and load it back:

```bash
$ docker save -o alpine.tar alpine
$ docker load -i alpine.tar
```

## Run

```bash
$ docker run --rm hello-world
$ docker run -it --rm alpine sh
$ docker run -d --name web -p 8080:80 nginx
$ docker run -d --name app -e MODE=prod -v app-data:/data alpine sleep infinity
$ docker run --rm -v "$PWD":/work -w /work alpine ls
```

| Flag | Effect |
| ---- | ------ |
| `--rm` | Delete the container when it exits |
| `-it` | Attach your terminal |
| `-d` | Run in the background |
| `--name` | Set the container name |
| `-p 8080:80` | Host port 8080 to container port 80 |
| `-e KEY=value` | Set an environment variable inside the container |
| `-v name:/path` | Mount a volume or a host directory at `/path` |
| `-w` | Working directory inside the container |

`-v "$PWD":/work` is a bind mount. The container sees your current directory at `/work`. A name with no slash, such as `app-data`, is a Docker volume.

## Containers

```bash
$ docker ps
$ docker ps -a
$ docker ps -q
$ docker start <container>
$ docker stop <container>
$ docker restart <container>
$ docker kill <container>
$ docker pause <container>
$ docker unpause <container>
$ docker rm <container>
$ docker rm -f <container>
$ docker rename <container> <new-name>
```

`ps` is running containers. `-a` includes stopped ones. `-q` prints only ids. `stop` sends the stop signal and waits. `kill` sends `SIGKILL`. `rm` removes a stopped container. `rm -f` stops it first, then removes it.

## Logs, shell, files

```bash
$ docker logs <container>
$ docker logs -f --tail 100 <container>
$ docker exec -it <container> sh
$ docker top <container>
$ docker stats
$ docker stats --no-stream
$ docker port <container>
$ docker inspect <container>
$ docker diff <container>
```

`logs -f` follows new lines. `--tail 100` is the last 100 lines. `exec` starts a shell in a container that is already running. `top` is the process list inside it. `stats` is live CPU and memory. `--no-stream` prints one sample and exits. `port` prints the published ports. `diff` lists files the container has added, changed, or deleted.

Copy a file in or out. The container path comes second when copying in, and first when copying out.

```bash
$ docker cp notes.txt <container>:/tmp/notes.txt
$ docker cp <container>:/tmp/notes.txt ./notes.txt
```

## Build

`docker build` reads a `Dockerfile` in the directory you give it. `.` is the current directory.

```bash
$ docker build -t <name>:<tag> .
$ docker build -t <name>:<tag> -f path/Dockerfile .
```

A Dockerfile is the build script. This one starts from Alpine, copies one file in, and sets the process to run:

```dockerfile
FROM alpine
COPY app /usr/local/bin/app
CMD ["app"]
```

`FROM` is the base image. `COPY` puts a file from the build directory into the image. `CMD` is the command `docker run` starts when you do not pass one.

Turn a changed container back into an image:

```bash
$ docker commit <container> <name>:<tag>
```

## Networks

```bash
$ docker network ls
$ docker network create <name>
$ docker network inspect <name>
$ docker network connect <name> <container>
$ docker network disconnect <name> <container>
$ docker network rm <name>
```

Containers on the same user-defined network reach each other by container name. `network rm` fails while a container is still attached.

Start a container on a network you created:

```bash
$ docker run -d --name app --network <name> alpine sleep infinity
```

## Volumes

```bash
$ docker volume ls
$ docker volume create <name>
$ docker volume inspect <name>
$ docker volume rm <name>
```

`inspect` prints the host path where Docker stores that volume. `rm` fails while a container still mounts it.

## Registry

```bash
$ docker login
$ docker logout
$ docker push <name>:<tag>
```

`login` stores credentials for a registry. The default registry is Docker Hub. `push` uploads an image you have already tagged with the registry name, for example `ghcr.io/<user>/<name>:<tag>`.

## Compose

Compose reads `compose.yaml` or `docker-compose.yml` in the current directory.

```bash
$ docker compose up
$ docker compose up -d
$ docker compose up -d --build
$ docker compose ps
$ docker compose logs
$ docker compose logs -f <service>
$ docker compose exec <service> sh
$ docker compose stop
$ docker compose start
$ docker compose restart
$ docker compose pull
$ docker compose down
$ docker compose down -v
```

`up` creates and starts the services. `-d` runs them in the background. `--build` rebuilds images first. `exec` opens a shell in a running service. `down` stops and removes the containers and the compose network. `-v` also removes volumes declared in the compose file.

Check the file without starting anything:

```bash
$ docker compose config
```

## Disk use and cleanup

```bash
$ docker system df
$ docker container prune
$ docker image prune
$ docker volume prune
$ docker network prune
$ docker builder prune
$ docker system prune
```

`system df` shows how much disk images, containers, and volumes are using. Each `prune` deletes unused objects of that kind and asks first. `image prune` removes dangling images only. `system prune` removes stopped containers, unused networks, dangling images, and build cache.

```bash
$ docker image prune -a
$ docker system prune -a
```

`-a` also removes images that no container is using, including tagged ones. Volumes are left alone unless you add `--volumes`.
