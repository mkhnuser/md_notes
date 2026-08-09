# GNU Linux Processes

## Processes

### Process ID

PID uniquely identifies a running process.

### uid

Processes inherit privileges from users who run them.
You can see who runs which processes using `ps`:

      ps -o pid,uid,gid,comm

### setuid

`setuid` changes process' `uid` which lowers process' privileges or escalates them.

### The Principle of Least Privilege

Processes inherit privileges from users who run them.
That's why you should assign a separate user and a separate group for each service you are running.
If a service process is compromised, no harm will be done to other parts of your system.

### procs

`procs` utility is a modern alternative for `ps` for process monitoring.

### CTRL + Z

Recall: `CTRL + Z` stops a process and puts it in the background to rest.
Allow a process to continue with either `fg %<job>` or `bg` after examining `jobs -l` output.

### killall

`killall` sends signals to processes by their command names.

### nice and renice

Understand: `nice -n +/-<nice value> command` applies only to the process in question.
No child processes are affected by niceness.

### cgroups

cgroups v2 allow one to limit resources a group of processes consumes.
Child processes are restricted just as their parents are.

## Process Isolation

`chroot` - change process's root directory.
`namespaces` (NS) - isolate one process from other processes.
`cgroups` (control groups) - limit process's resource consumption: CPU, Memory, I/O, etc.
