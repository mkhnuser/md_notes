# GNU Linux File System

## Common commands

### mv and cp are destructive

`mv` and `cp` commands will overwrite a destination file if one exists.
Because of this, consider adding `alias mv= mv -i` to your `.bashrc`.

### cp with archiving

Consider using `cp -a` to preserve the original metadata.

### Finding Files

One can use `plocate` database-based search or a `find` command to search for files.
Understand: you can only locate files to which you have access.
Further, `plocate`'s database has to be up-to-date.

### See free disk space

`df -h`

### See disk usage

`du -d 1 -h`

### Finding disk consumption with find command

Refer to the "Linux Bible", 11th edition, Chapter 13 discussion on this.

## Inodes

### Overview

Inode stands for an index node.
When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

### Inodes and file systems

Each file system will have its own set of inodes.

## Partitions

### How does one handle a new disk?

1. Partition a new disk.

        parted
        fdisk

2. Create a file system on the disk.

        mkfs

3. Mount the new file system on the already existing directory in your file system.

        mount

Having done that,
every file that is be created under the mount point,
will be stored in the particular partition which is associated with the mounted file system.

4. Unmount a file system, and potentially safely remove a disk.

        umount

### Partition types

Each partition will have a type: swap, LVM, Linux, etc.
Partition type is different from a file system type.

### Automatic Mounts

`/etc/fstab` file will contain partitions which are mounted automatically.

### Reflecting partition changes

Once partitions have been created, use `partprobe` to reflect the changes in the OS.
After it, confirm that partitions have been applied:

        partprobe /dev/sdb
        grep sdb /proc/partitions

## LVM

### Objective of LVM

Suppose you are about to run out of space on your hard drive.
Without LVM, you have to copy the data to another drive,
and then mount the drive, which leads to a downtime.

LVM resolves this problem: LVM allows one to resize the file system with ease.

### LVM structure

1. Physical volumes.
2. Volume groups.
3. Logical volumes.

PV -> VG -> LV.

### LVM flow

A physical volume set up:

1. Creating a partition with the partition type of LVM.
2. Create a physical volume.

After a physical volume is created, volume groups and logical volumes can be configured:

1. Create a volume group.
2. Create a logical volume.
3. Examine `/dev/mapper` for the newly created logical volume.
4. Create a file system for a logical volume.
5. Mount the logical volume onto an already existing directory.
6. Potentially modify `/etc/fstab` for a logical volume automount.

## Mounting file systems

### Kernel and mount

When you mount a file system, Kernel loads a module to handle the file system.

### Device UUIDs

Consider the usage of UUID for a device identification instead of `/dev/sd(a?)`, and other names,
since a UUID does not rely on the order in which devices are loaded.
To see device UUIDs: `blkid`.

### umount

To unmount a file system, make sure:

1. Close the shell which is open within the file system.
2. Close the files which are open within the file system.
