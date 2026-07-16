# Linux

## Users and permissions

### Services

Ideally, each service should have its own user and group.

### Permission flags

* r = 4 = 100;
* w = 2 = 010;
* x = 1 = 001;

### Permission commands

* chmod - change file permissions;
* chown - change an owner or a group of a file.

### sudoers file

To change this file, use `sudo visudo` only.

## File System

### Inodes

When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

## Devices and File Systems

Linux lists all available devices in `/dev` directory.
Here is the list of available devices: *c* (character device), *b* (block), *s* (socket), *p* (pipe).

Linux partitions disks and stores Partition Table on a disk. Essentially, a partition sets a boundary on a disk.
A filesystem creates file and directory hierarchy on your system.
You create a particular filesystem on a particular partition after you've created this partition.
Any present data is destroyed if you create a new fs.

The process of connecting a fs to a running system is called mounting.
You mount a specific device (a disk or a partition) on a specific location on your fs called mount point.
Mount point is a directory.

Use LVM for flexible disk management:

* you treat disk partitions as physical volumes;
* you connect physical volumes to a volume group(s);
* you create logical volumes out of a volume group.
