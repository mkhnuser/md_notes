# Linux

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
