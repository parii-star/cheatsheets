# Docker Cheat Sheet

> **Goal:** Learn the most common Docker commands clearly enough to run containers and debug simple setups as a beginner.

This cheat sheet is a beginner-friendly reference for images, containers, volumes, ports, and Docker Compose.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[image]` | replace with an image name, such as `nginx` or `python` |
| `[container]` | replace with a container name or ID |
| `[name]` | replace with a custom container, volume, or network name |
| `[path]` | replace with a file or directory path |
| `[port]` | replace with a port number such as `80` or `3000` |

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Setup](#setup) | check Docker is installed |
| [Images](#images) | download, list, and build images |
| [Containers](#containers) | run and manage containers |
| [Ports And Volumes](#ports-and-volumes) | publish ports and keep data |
| [Docker Compose](#docker-compose) | run multi-container apps |
| [Inspect And Logs](#inspect-and-logs) | debug what is happening |
| [Cleanup](#cleanup) | remove unused Docker resources |

## Setup

| Command | Clear Description |
|---|---|
| `docker --version` | Show the installed Docker version. |
| `docker info` | Show Docker daemon and system details. |
| `docker help` | Show the main Docker help screen. |

Example:

```bash
docker --version
docker info
```

## Images

| Command | Clear Description |
|---|---|
| `docker pull [image]` | Download an image from Docker Hub. |
| `docker images` | List images stored on your machine. |
| `docker build -t [name] .` | Build an image from a Dockerfile in the current folder. |
| `docker tag [image] [name]` | Give an image a new name or label. |

Example:

```bash
docker pull nginx
docker build -t my-app .
```

## Containers

| Command | Clear Description |
|---|---|
| `docker run [image]` | Start a new container from an image. |
| `docker run -it [image] sh` | Start an interactive container with a shell. |
| `docker ps` | List running containers. |
| `docker ps -a` | List all containers, including stopped ones. |
| `docker stop [container]` | Stop a running container. |
| `docker start [container]` | Start a stopped container again. |
| `docker restart [container]` | Restart a container. |
| `docker rm [container]` | Remove a stopped container. |
| `docker exec -it [container] sh` | Open a shell inside a running container. |

Example:

```bash
docker run -d --name web -p 8080:80 nginx
docker ps
docker exec -it web sh
```

## Ports And Volumes

| Command | Clear Description |
|---|---|
| `-p 8080:80` | Map a local port to a container port. |
| `-v [path]:/data` | Mount a local folder into a container. |
| `docker volume create [name]` | Create a named volume for persistent data. |
| `docker volume ls` | List Docker volumes. |
| `docker network ls` | List Docker networks. |

Example:

```bash
docker run -d --name app -p 3000:3000 -v "$PWD/data:/data" my-app
```

## Docker Compose

| Command | Clear Description |
|---|---|
| `docker compose up` | Start services defined in compose files. |
| `docker compose up -d` | Start services in the background. |
| `docker compose down` | Stop and remove compose services. |
| `docker compose ps` | Show services started by Compose. |
| `docker compose logs` | Show logs for compose services. |

Example:

```bash
docker compose up -d
docker compose logs
```

## Inspect And Logs

| Command | Clear Description |
|---|---|
| `docker logs [container]` | Show container logs. |
| `docker logs -f [container]` | Follow logs live. |
| `docker inspect [container]` | Show detailed container or image information. |
| `docker stats` | Watch container resource usage live. |

Example:

```bash
docker logs -f web
docker inspect web
```

## Cleanup

| Command | Clear Description |
|---|---|
| `docker rm -f [container]` | Force remove a container. |
| `docker image rm [image]` | Remove an unused image. |
| `docker volume rm [name]` | Remove a named volume. |
| `docker system prune` | Remove unused Docker resources. Use carefully. |

Example:

```bash
docker system prune
```

## Where DevOps Engineers Use This

Use Docker when you want the same app to run the same way on a laptop, in CI, and on servers.

- Build test and release images in CI/CD pipelines.
- Run supporting services such as databases, Redis, or Nginx during local development.
- Package and ship applications in a repeatable way.
*** Update File: /home/paripatodi/Documents/cheatsheets/linux-commands-cheatsheet.md