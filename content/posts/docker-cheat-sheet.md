+++
date = '2025-10-01T09:40:29+01:00'
draft = false
tags = ['Docker', 'Python']
title = 'Docker Cheat Sheet'
+++

Dockerfiles: plain text instructions to automatically make images.

Docker containers: the active, running parts of Docker that do something.

Docker images: pre-built environments and instructions that tell a container what to do.

### Check if a docker container is running
```bash
docker inspect -f {{.State.Running}} container_id
```
### To list all Docker containers you can use one of the following commands:
```bash
docker ps -as
docker ps -aq
docker ps -a
```
### List all Docker images:
```bash
docker images ps
docker images -a
```
### Remove a specific docker container
```bash
docker rm <container_id>
```
### Force remove all Docker containers
```bash
docker rm -f $(docker ps -a -q)
```
### Remove a specific Docker image
```bash
docker rmi <image_id>
```
### Force remove all Docker images
```bash
docker rmi -f $(docker images -q)
```
### Running docker with auto remove containers
```bash
docker run --rm <image_name> <CMD>

# Execute shell in Docker container
docker exec -it <container_id> /bin/bash

# Execute shell in container using Docker Compose
docker-compose exec <service_name> /bin/bash

# Dockerfile example
FROM r-base:latest  # for python 2.7 (FROM python:2.7)
# Set a default user. Available via runtime flag `--user docker`;
# Add user to 'staff' group, granting them write
# privileges to /usr/local/lib/R/site.library;
#
# User should also have & own a home directory.
RUN useradd docker \
    && mkdir /home/docker \
    && chown docker:docker /home/docker \
    && addgroup docker staff
RUN apt-get update && apt-get install vim -y
RUN pip install matplotlib
RUN pip install ipython
COPY . /src
CMD [\"R\", \"/src/read_data.R\"]
```
### Sharing data between the host system and a docker container
The easiest way to share a data between a Docker container and the host system is to use docker’s volumes. To do this simply run your docker container using the `-v` option to mount a local host system directory e.g: `data` to the container’s directory `/home/user/data`.

Please note that if the destination does not exists it will be created by the the docker command. Furthermore, docker only accepts a full path to a local host system directory and from this reason we need to prefix the `data` directory with $PWD/ environmental variable which returns a full path to a current working directory:
```
# PWD=/home/user/data
docker run -v $PWD:/home/user/data -it image_name /bin/bash
root@29b320e5ebbf:/#
```
Additionally, docker containers run as the root user, this means that any files created or modified by the container will thus become owned by the root user, even if you are sharing a volume or even after quitting the container. To avoid this problem, it is necessary to run the container using a non-root user.

To create a user in your container simply add the following to your Dockerfile:
```
# Set a default user. Available via runtime flag `--user docker`;
# Add user to 'staff' group;
#
# User should also have & own a home directory.
RUN useradd docker \
    && mkdir /home/docker \
    && chown docker:docker /home/docker \
    && addgroup docker staff
```
Once done, to run the container a that user execute:
`docker run --rm -it -v $PWD:/home/$USER/ -u docker python script_name.py`
### Remove exited containers
```bash
docker rm -f $(docker ps -f status=exited -q)
```