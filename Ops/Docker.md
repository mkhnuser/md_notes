# Docker

Docker has three types of volumes: anonymous, named and bind mount. You can use bind mount for instant code updates inside of your container. Docker compose works only on one host; use k8s for distributed computing.

Suppose you've got Docker Compose and you need to wait till some service starts up.
Then you can specify `sleep 10` before executing a command which requires another service.
