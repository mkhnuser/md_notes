# Debugging

## Logs

Structured logs with the correct logging level allow you to
easily assess what's going on with you program.

## Debugging Utilities

### Debugging

`rr` utility allows you to go up the execution thread.
It's extremely similar to `gdb`.

### Syscalls

`strace` utility shows system calls which a process makes.
`bpfstace` utility uses eBPF.
`biolatency` utility shows disk access times.
`opensnoop` utility shows every open call which made on your system.

### Networking

`tcpdump` utility allows one to analyze network traffic.
`wireshark` utility allows one to analyze network traffic using GUI.

### Sanitizers

Sanitizers allow one to automatically check their programs
for common bugs.

### Valgrind

Valgrind allows one to execute their program to see if it contains common bugs.

## Links

https://www.youtube.com/watch?v=8VYT9TcUmKs&t=1082s
https://missing.csail.mit.edu/2026/debugging-profiling/
