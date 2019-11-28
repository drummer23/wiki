# Concept

An Dockerfile builds an Image which runs a Container

![](resources/docker_concept.png)

## Docker-Compose

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services

## Commands

```bash
docker build
docker run
docker ps      # show running processes
```

```bash
docker-compose build
docker-compose up [--build] [--detach]
docker-compose stop
docker-compose run {containername} {bin/console cache:clear}
```

```bash
#stop all containers:
docker stop $(docker ps -a -q)

#stop all containers by force
docker kill $(docker ps -q)

#remove all containers
docker rm $(docker ps -a -q)

#remove all docker images
docker rmi $(docker images -q)

#purge the rest
docker system prune --all --force --volumes
```
