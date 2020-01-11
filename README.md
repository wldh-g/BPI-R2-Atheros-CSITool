# BPI-R2 Atheros CSITool Kernel

<a href="https://travis-ci.com/wldh-g/BPI-R2-Atheros-CSITool" target="_blank">
    <img src="https://travis-ci.com/wldh-g/BPI-R2-Atheros-CSITool.svg?branch=5.4-main" alt="Build status 5.4-main" />
</a>

This is a Linux **5.4** kernel source for Banana Pi R2 (BPI-R2) which includes [Atheros CSI tool](https://github.com/xieyaxiongfly/Atheros-CSI-Tool).

### How To Build and Install?

#### A - Install Prebuilts

+ [Debian Image](https://go.wldh.org/r2-atheros-img)\
  This image is a result of `dd` of 8GB sdcard and only kernel is installed. ID: `root` \ PWD: `bananapi`.
+ [Debian Appready Image](https://go.wldh.org/r2-atheros-full-img)\
  This is also an image of 8GB sdcard, and all prerequisites are installed. ID: `momo` \ PWD: `momo`.\
  Default shell is [fish](https://fishshell.com/) shell, you can change it to `bash` by typing `chsh momo /bin/bash`.\
  There is CSI-Collector app on home directory. To use them, read [this readme](https://github.com/wldh-g/BPI-R2-Atheros-CSITool-App).
+ [Build Output](https://go.wldh.org/r2-atheros-patch)\
  This is a latest csitool-runability-checked output of "pack" option at method B.
  
After install the sdcard image, you can extend your partition to the end of the sdcard using below commands in root shell:

```sh
apt-get install cloud-guest-utils
growpart /dev/mmcblk0 2
resize2fs /dev/mmcblk0p2
```

#### B - Build Yourself

On a x86/x64-host you need cross compile tools for the armhf architecture (`bison` and `flex` package are needed for kernels >=4.16):

```sh
sudo apt install ccache gcc-arm-linux-gnueabihf libc6-armhf-cross u-boot-tools bc make gcc libc6-dev libncurses5-dev libssl-dev bison flex
```

If you build it directly on the BananaPi-R2 you do not need the crosscompile-packages `gcc-arm-linux-gnueabihf` and `libc6-armhf-cross`

Then build using with default configuration:

```sh
./build.sh
```

The option "pack" creates a tar.gz-file which contains folders `BPI-BOOT` (content of boot-partition aka `/boot`) and `BPI-ROOT` (content for rootfs aka `/`).

Simply backup your existing `/boot/bananapi/bpi-r2/linux/uImage` and unpack the content of these 2 folders to your system.

You can also install direct to sd-card which makes a backup of kernelfile, here you have to change your `uEnv.txt` if you use a new filename (by default it's containing kernelversion.)

### How To Get the CSI?

Look [here](https://github.com/wldh-g/BPI-R2-Atheros-CSITool-App#readme).  

### Authors and License

- Base Linux Kernel: Linux Kernel Contributors, GPL-2.0, optimized and extended for BPI-R2 by [frank-w](https://github.com/frank-w).

- ath9k CSITool Driver: Yaxiong Xie ([Project Homepage](https://wands.sg/research/wifi/AtherosCSI/)).

