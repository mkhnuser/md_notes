# GNU Linux Devices

## Hardware to Device

UDev service adds and removes devices in `/dev` directory.
As the hardware is plugged in, UDev adds an appropriate device in `/dev`.
If a device contains a filesystem, modern Linux distributions try to mount it.

## dmesg

`sudo dmesg | less` displays which devices have been found
and which drivers have been loaded during the kernel boot.

## ls* commands

The commands below display PCI buses, USB devices, and CPUs which are found.

    lspci | less
    lsusb | less
    lscpu | less

## Kernel Modules

Kernel is provided with optional modules which one can load.
Often, by modules we mean drivers for hardware.

## Listing Loaded Modules

To list loaded modules, issue: `lsmod`.
