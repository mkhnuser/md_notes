# Docker

## Overview

Docker is built on top of chroot, namespaces & cgroups.

chroot, as the name implies, changes the root directory of the current process.
namespaces isolate what the current process has access to.
cgroups limit the current process's resources.

## Volumes

Docker has three types of volumes:

* Anonymous;
* Named;
* Bind mount.

You can use bind mounts for instant code updates inside of your container for debugging purposes, for example.

## Docker Compose

Docker compose only works on one local host;
use k8s for distributed computing.

## Docker Networking

Suppose you've got Docker Compose and you need to wait till some service starts up.
Then you can specify `sleep 10` before executing a command which requires another service.

The default bridge network does not have a DNS resolver: you can only use IP addresses.
If you want to use container names instead of IP addresses, create your own user-defined bridge net.

## Docker Commands

### Docker Attach & Docker Exec

Attach attaches you to an already existing process,
whereas Exec creates a new one.

Be careful when you exit a process to which you've been attached.
If it was the only running process, then the container will stop.

### Docker Pause

Pauses all the running processes inside a container.

### Docker History & Docker Info

History shows you the history of an image;
where Info shows you how Docker is configured.

### Docker Search

Search on a docker registry.
