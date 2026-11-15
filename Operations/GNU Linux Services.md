# GNU Linux Services

## Overview

Linux groups applications into a set of services.
These services can then be managed by the target units, or also known as run levels.

## Operating system start up

The Linux kernel will have a process id of 0.

A initialization system process will be spawned with a PID of 1 and PPID of 0.
`Systemd` systems will have the process called `systemd`,
whereas `SysVInit` will have the process named `init`.
