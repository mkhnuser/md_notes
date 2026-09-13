# GNU Linux File System

## Common commands

### mv and cp are destructive

`mv` and `cp` commands will overwrite a destination file if one exists.
Because of this, consider adding `alias mv= mv -i` to your `.bashrc`.

### cp with archiving

Consider using `cp -a` to preserve the original meta information.

### Finding Files

One can use `plocate` database-based search or a `find` command to search for files.
See "The Linux Bible", 11th edition, Chapter 5, Finding Files discussion.
Beware that you only are only able to locate files to which you normally have access.

## Inodes

### Overview

When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

## Partitions

### Overview

A storage device is broken up into partitions.
`/etc/fstab` file will contain partitions which are mounted automatically.

### How does one attach new storage devices?

1. Physically attach a storage device to your computer;
2. Partition a new disk;

        See parted or fdisk command.

3. Create a file system on the disk;

        See mkfs command.

4. Mount the file system.
