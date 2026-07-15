# Computer Organization

## History

### The first computer

https://en.wikipedia.org/wiki/ENIAC

### Transistors

Before transistors were invented in 1947, computers used vacuum tubes.
Roughly speaking, 6 transistors = one logical gate.
1nm transistor size is planned for 2027.

### Moore's Law

The number of transistors in an integrated circuit doubles every two years.
Physics poses a physical limit on this law.

## The physical booting process

1. Power On Self Test (POST):

        BIOS or UEFI tests that a computer components work correctly.
        https://en.wikipedia.org/wiki/Power-on_self-test

2. Boot loader accesses the hard drive to initialize an OS core.
3. An OS core takes over.
4. An OS core uses drivers to initialize peripherals.

## Processor Modes

A processor operates in two modes:

1. User mode:

        User mode processes make system calls to the kernel when a privileged access is required.

2. Kernel mode.

        Kernel mode has direct access to the file system, network drivers, memory, etc.
