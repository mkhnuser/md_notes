# GNU Linux Devices

## What do we mean by devices?

Devices might represent:

* Disk partitions.
* Periphery: a mouse, a keyboard, etc.
* Network devices.

## Hardware to device mapping & auto mount process for file systems

As the hardware is plugged in, Linux adds an appropriate device in `/dev`.
`UDev` service is responsible for this translation.
If a device contains a file system, modern Linux distributions will try to mount it.

## dmesg

`sudo dmesg | less` displays:
* Which devices have been found.
* Which drivers have been loaded during the kernel boot.

## ls* commands

The commands below display PCI buses, USB devices, and CPUs which are found.

    lspci | less
    lsusb | less
    lscpu | less

## Kernel Modules

Kernel is provided with optional modules which one can load.
Often, by modules we mean drivers for hardware.

## Listing Loaded Modules

To list loaded modules: `lsmod`.
