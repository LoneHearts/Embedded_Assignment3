Assignment 3

First install dependencies

```
apt install git bc bison flex libssl-dev make libc6-dev libncurses5-dev
```

Install toolchain

```
git clone https://github.com/raspberrypi/tools
```

then add to the PATH environment variable :

```
arm-bcm2708/arm-linux-gnueabihf/bin
```

Get kernel source files

```
git clone --depth=1 https://github.com/raspberry/linux
```

Compile Kernel for Pi 4

```
KERNEL=kernel7l  ( for Pi 4 )
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2711_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs -j 6 ( cause i have 4 logical processors )
```

Launch my kernel with Qemu ( with the raspiban buster image )

```
 .\qemu-system-arm -M versatilepb -cpu arm1176  -hda .\2020-02-13-raspbian-buster-full.img -kernel .\zImage -append 'root=/dev/sda1' -no-reboot
```

note :
On the screenshot you can see that the kernel doesn't support GUI
