# GNU Linux Devices

## Hardware to device & automount

As the hardware is plugged in, Linux adds an appropriate device in `/dev`.
`UDev` service is responsible for this translation.
If a device contains a file system, modern Linux distributions will try to mount it.

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

To list loaded modules: `lsmod`.
