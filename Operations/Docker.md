# Docker

## Overview

Docker is built on top of `chroot`, `namespaces` & `cgroups`.

`chroot` - change process's root directory.
`namespaces` (NS) - isolate one process from other processes.
`cgroups` (control groups) - limit process's resource consumption: CPU, Memory, I/O, etc.

## Volumes

Docker has three types of volumes:

* Anonymous;
* Named;
* Bind mount.

### Anonymous Volumes

Anonymous volumes are given a random name.
Anonymous volumes are deleted if a container which was run with `--rm` flag exits.

### Bind Mounts

You can use bind mounts for instant code updates inside your container for debugging purposes, for example.

An example of a bind mount:

    docker run --mount type=bind,source="$(pwd)"/dist,target=/usr/share/nginx/html -p 8080:80 nginx:latest

## Docker Networking

### Networking Basics

Containers have access to the Internet by default.
However, containers are isolated from each other by default.
To allow contains access each other, attach them to a common network.
Docker Compose creates a common network for a compose project.

### Default Bridge Network

The default bridge network is considered a legacy:
it does not provide DNS resolution between containers,
so you can only use container's IP addresses.

It does not isolate containers of your different projects as well,
so they all share the same network, which is bad in terms of security.

If you want to use container names instead of IP addresses, create a user-defined bridge network.

## Dockerfile

### ARG vs ENV

`ENV` directive specifies environment variables within your container,
whereas `ARG` allows one to pass variables to the build process.
`ARG` does not set variables within a container.

Example of a Dockerfile with `ARG`:

    # Allows one to pass an argument to the build process.
    ARG APP_VERSION=latest
    # Use an argument within a build process.
    ENV APP_VERSION=${APP_VERSION}

The one can start the build process and pass the argument:

    docker build --build-arg APP_VERSION=1.0 -t superapp:1.0 .

### Multi-stage Builds

Multi-stage builds are useful if you want to increase security of you application:

1. Install the dependencies in the build step,
2. Discard the dependency installer software in the production step.

## Docker Commands

### Overview

Some useful Docker commands follow next.

### Docker Attach & Docker Exec

`attach` attaches you to an already existing process, whereas `exec` creates a new one.

Be careful when you exit a process to which you've been attached.
If it was the only running process, then the container will exit.

### Docker Pause

Pauses all the running processes inside a container.

### Docker History & Docker Info

`history` shows you the history of an image;
whereas `info` shows you how Docker is configured.

### Docker Search

Search on a docker registry.

### Docker Scout

Scout is a built-in vulnerability scanner.

### Docker Commit

Create a new image based on a used, modified container:

    docker commit my_container my_image:latest

## Docker Compose

Docker Compose works only on one host; use k8s for distributed orchestration.

## Docker Compose Commands

### Overview

All commands apply to a specific `docker-compose.yml` project.

### Docker Compose Ps

See the compose project container status.

### Docker Compose Down

Stops and deletes all containers.

### Docker Compose Stop

Just stops all containers.

### Docker Compose Restart

Restart all containers.

### Docker Compose Logs

See logs of the compose project.

## Kompose Project

Kompose Project turns your Docker Compose config files into Kubernetes config files.
