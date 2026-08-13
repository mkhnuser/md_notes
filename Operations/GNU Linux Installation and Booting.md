# GNU Linux Installation and Booting

## Booting

When you press the power button, here is what happens:

1. Power On Self Test (POST):

        BIOS or UEFI tests that a computer components work correctly.
        https://en.wikipedia.org/wiki/Power-on_self-test

2. The processor triggers ROM on a motherboard which contains BIOS or UEFI.
3. BIOS or UEFI is loaded from ROM.
4. BIOS or UEFI runs a bootloader, for example, GRUB2.

        Usually BIOS does not run an OS directly.

# TODO: Learn about initrd.

5. A bootloader loads OS kernel into the memory.
6. System initialization happens, for example, systemd is used.
