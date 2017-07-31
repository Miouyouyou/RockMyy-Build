If you appreciate this project, support me on Patreon !

[![Patreon !](https://raw.githubusercontent.com/Miouyouyou/RockMyy/master/.img/button-patreon.png)](https://www.patreon.com/Miouyouyou)

About
-----

This repository hosts patched mainline kernels for RK3288 built using
the VPU branch of
[RockMyy](https://github.com/Miouyouyou/RockMyy/tree/VPU).

This branch is made to test the Video Processing Unit driver, in order
to benefit from hardware accelerated video encoding and decoding
features.

Some knowledge about your system bootloader configuration is required.
Generally, the bootloader is configured through /boot/extlinux.conf but
that can change. Just read the documentation of your distribution if
you don't know how to install a new kernel manually.

Quick and (Very) Dirty installation method
------------------------------------------

> BACKUP YOUR /boot FOLDER BEFORE. And prepare an UART cable, just in case
things go terribly wrong.

To use it on your RK3288 board (ASUS Tinkerboard, MiQi, Firefly, ...) :
* clone this project
* copy `lib/*` into your board `/lib/` directory
* copy `usr/*` into your board `/usr/` directory
* copy `boot/*` into your board `/boot/` folder

And then configure your bootloader so that it :
* boots the /boot/zImage
* uses the DTB file appropriate for your board

Appropriate DTB files being :
* **rk3288-miqi.dtb** for MQMaker MiQi boards
* **rk3288-tinkerboard.dtb** for ASUS Tinkerboard boards
* **rk3288-firefly.dtb** for Firefly boards
* **rk3288-firefly-reload.dtb** for Firefly Reload boards

This roughly equates to :
```bash
git clone --depth 1 https://github.com/Miouyouyou/RockMyy-Build &&
cd RockMyy-Build &&
chown root:root -R * &&
cp boot/* /boot/ &&
cp -r lib/* /lib/ &&
cp -r usr/* /usr/
```

If your bootloader is configured to boot /boot/zImage with the
appropriate /boot/rk3288-???.dtb file, just reboot and enjoy your new
kernel.

Debian packages
---------------

Armbian currently provide premade Debian packages of kernels for
Rockchip systems including most of the patches included here.
