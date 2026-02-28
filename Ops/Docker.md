# Docker

## Overview

Docker is built on top of `chroot`, `namespaces` & `cgroups`.

`chroot` - change process's root directory.
`namespaces` - isolate one process from other processes.
`cgroups` - limit process's resource consumption: CPU, Memory, I/O.

## Volumes

Docker has three types of volumes:

* Anonymous;
* Named;
* Bind mount.

You can use bind mounts for instant code updates inside your container for debugging purposes, for example.

An example of a bind mount:

    docker run --mount type=bind,source="$(pwd)"/dist,target=/usr/share/nginx/html -p 8080:80 nginx:latest

Anonymous volumes are given a random name.
Anonymous volumes are deleted if a container which was run with `--rm` flag exits.

## Docker Compose

Docker Compose works only on one host; use k8s for distributed orchestration.

## Docker Networking

In Docker, containers have access to the Internet by default.
However, containers are isolated from each other.
To allow contains access each other, attach them to a common network;
Docker Compose creates a common network by default.

Understand: the default bridge network is considered a legacy.
It does not provide DNS resolution between containers,
so you can only use container's IP addresses.
It does not isolate containers of your different projects,
they all share the same network, which is bad in terms of security.

If you want to use container names instead of IP addresses,
create user-defined bridge network.

## Multi-stage Builds

Multi-stage builds are useful if you want to increase security of you application:
Install the dependencies in the build step,
Discard the dependency installer software in the production step.

## Docker Commands

### Docker Attach & Docker Exec

Attach attaches you to an already existing process, whereas Exec creates a new one.

Be careful when you exit a process to which you've been attached.
If it was the only running process, then the container will exit.

### Docker Pause

Pauses all the running processes inside a container.

### Docker History & Docker Info

History shows you the history of an image;
where Info shows you how Docker is configured.

### Docker Search

Search on a docker registry.

### Docker Scout

Scout is a built-in vulnerability scanner.
