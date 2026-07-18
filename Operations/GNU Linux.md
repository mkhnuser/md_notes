# GNU Linux

## System Initialization

When you press the power button, here is what happens:

1. Power On Self Test (POST):

        BIOS or UEFI tests that a computer components work correctly.
        https://en.wikipedia.org/wiki/Power-on_self-test

2. The processor triggers ROM on a motherboard which contains BIOS or UEFI.
3. BIOS or UEFI is loaded from ROM.
4. BIOS or UEFI runs a bootloader, for example, GRUB2.

        Usually BIOS does not run an OS directly.

# TODO: Learn about initrd.

5. A bootloader loads OS kernel into the memory.
6. System initialization happens, for example, systemd is used.

## Users and permissions

### How do you run services with respect to users and groups?

Understand: a process inherits privileges of a user who runs this process.
Ideally, each service should have its own user and group when it runs.
It allows one to restrict what a service can and cannot do.

### Permission flags

* r = 4 = 100;
* w = 2 = 010;
* x = 1 = 001;

### Permission commands

* chmod - change file permissions;
* chown - change an owner or a group of a file.

### sudoers file

Sudoers file allows you to control who has access to `sudo`.
It also allows you to restrict `sudo` usage for a group or a user.
To change this file, use `sudo visudo` only.

## File System

### Inodes

When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

## Processes

### uid

Processes inherit privileges from users who run them.
You can see who runs which processes using `ps`:

      ps -o pid,uid,gid,comm

That's the reason why you should run processes rootless.

### setuid

`setuid` changes process' `uid` which lowers process' privileges or escalates them.
