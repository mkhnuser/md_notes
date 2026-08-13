# GNU Linux Permissions

## Permissions

### How do you run services with respect to users and groups?

Understand: a process inherits privileges of a user who runs this process.
Ideally, each service should have its own user and group when it runs.
It allows one to restrict what a service can and cannot do.

### What happens when a user runs a command?

When a user runs a command,
then a process which represents this command inherits user's permissions.

If a user has a read access or a write access to a file,
then the process will also have it.

### Permission flags

* r = 4 = 100;
* w = 2 = 010;
* x = 1 = 001;

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

## ACL

### Overview

ACL stands for access control list.
ACL allows one to fine-tune access to files or directories to a specific user or a specific group.
ACL has to be enabled on the filesystem during mounting phase.

## Set user id, set group id, set sticky bit

SUID allows one to obtain permissions of a user who owns a file.
SGUID allows one to collaborate within a given directory.
Finally, a sticky bit allows one to restrict deletion within a directory.
