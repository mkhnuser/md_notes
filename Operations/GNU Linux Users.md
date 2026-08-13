# GNU Linux Users

## Users

### Who is logged in?

To see logged in users:

    who -aH

### /etc/passwd file

`/etc/passwd` file contains user accounts.

### the same uid for two different usernames

Two different usernames might be assigned to the same uid.
Examine `-u` and `-o` options for `useradd` command.

### Group

By default, on many distributions, a user will be given a primary group of the same name.

### Why do you need groups?

One can use groups to efficiently share directories.

### root user

Fedora and Ubuntu give access to `sudo` to the first user created on a system.

### su command

`su -` opens a login shell, so the environment will be initialized appropriately.

      See bash notes on the difference between an interactive shell and a login shell.

One can use `su` command applied to any user on the system.

### sudo and resource creation

Observe: if one creates a file with `sudo`, a root user will be an owner.

### sudo vs root

Advantages of using `sudo` are:

1. One does not have to know the root password. Only a user's password will be prompted for.
2. One has access only to a subset of root privileges.
3. Observability of actions.

### sudoers file

Sudoers file allows you to control who has access to `sudo` and which rights are granted.
To change this file, use `sudo visudo` only.

### /etc/skel

`/etc/skel` directory contains files
which are copied into a new user's home directory when a user is created.
