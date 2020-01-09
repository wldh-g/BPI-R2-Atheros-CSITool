# BPI-R2 Atheros CSITool Kernel

<a href="https://travis-ci.com/wldh-g/BPI-R2-Atheros-CSITool" target="_blank">
    <img src="https://travis-ci.com/wldh-g/BPI-R2-Atheros-CSITool.svg?branch=5.4-main" alt="Build status 5.4-main" />
</a>

This is a Linux **5.4** kernel source for Banana Pi R2 (BPI-R2) which includes [Atheros CSI tool](https://github.com/xieyaxiongfly/Atheros-CSI-Tool).

### How To Build and Install?

#### A - Install Prebuilts

+ [Debian Image](https://go.wldh.org/r2-atheros-img) : This image is a result of `dd` of 8GB sdcard.
+ [Build Output](https://go.wldh.org/r2-atheros-patch) : This is a latest output of "pack" option at method B.

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

### License

GPL-2.0
