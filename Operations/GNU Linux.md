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

### Who is logged in?

To see logged in users:

    who -aH

### Groups

By default, on many distributions, a user will be given a group of the same name.

### How do you run services with respect to users and groups?

Understand: a process inherits privileges of a user who runs this process.
Ideally, each service should have its own user and group when it runs.
It allows one to restrict what a service can and cannot do.

### Permission flags

* r = 4 = 100;
* w = 2 = 010;
* x = 1 = 001;

# TOOD: Learn about a sticky bit, set UID, set GID.

### What do these flags mean for a file or a directory?

1. Read permission.

        For a file, one can view its content.

        For a directory, one can view its subdirs and files,
        but not necesserily what's inside these subdirs and files.

2. Write permission.

        For a file, one can modify its content, rename, and delete it.

        For a directory, one can create and delete files or subdirectories within it.

3. Execute permission.

        For a file, one can run this file.

        For a directory, one can:

        a. Change to the directory as the current directory.
        b. Search through the directory.
        c. Execute a program from the directory.
        d. Access file metadata (file size, time stamps, and so on) of files in that directory.

### chmod

One can use `chmod` if one owns a file or if a user is a superuser.
One can use `chmod` recursively `chmod -R 755 $HOME/dir`.

### chown

One can use `chown` to change owner or a group of a file.
One can use `chown` recursively `chown -R joe:joe /mnt/mystuff`.

      The command above will make joe user and joe group own a mount point.

### umask

One can use `umask` to change the default permissions.

### sudoers file

Sudoers file allows you to control who has access to `sudo`.
It also allows you to restrict `sudo` usage for a group or a user.
To change this file, use `sudo visudo` only.

## File System

### mv and cp are destructive

`mv` and `cp` commands will overwrite a destination file if one exists.
Because of this, consider adding `alias mv= mv -i` to your `.bashrc`.

### cp with archiving

Consider using `cp -a` to preserve the original metainformation.

### Inodes

When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

## Processes

### uid

Processes inherit privileges from users who run them.
You can see who runs which processes using `ps`:

      ps -o pid,uid,gid,comm

That's the reason why you should run processes rootless - the principle of least privilege.

### setuid

`setuid` changes process' `uid` which lowers process' privileges or escalates them.

## Process Isolation

`chroot` - change process's root directory.
`namespaces` (NS) - isolate one process from other processes.
`cgroups` (control groups) - limit process's resource consumption: CPU, Memory, I/O, etc.

## Network Isolation

`ip netns` - create a network namespace to which network interfaces can be attached.

## References

Consult "The Linux Bible", 11th edition.
