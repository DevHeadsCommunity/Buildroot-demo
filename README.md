# Buildroot-demo

This guide provides instructions for a Buildroot demo on Raspberry Pi Zero W 2, where we will customise the root password and update the banner.

## Installation

get the official buildroot repository cloned on you local system by doing a git clone 

```bash
git clone https://github.com/buildroot/buildroot.git
```

## Build Process

we will list the available defconfigs with the following, find if your target board's defconfig exists.

```bash
cd buildroot/
make list-defconfigs
```
next we will be selecting the our target and it will copy the defconfig from the configs folder to .config file which buildroot will further use for the menucofnig.

```bash
make raspberrypizero2w_defconfig
```

next we can run make menuconfig command 

```bash
make menuconfig
```
here is the beginner friendly keybinding which is configured for menuconfig  
going back to the pervious menu:  [esc][esc]  
searching console:                [/]  
select a option :                 [y]  
unselect a option :               [n]  
use  [tab] to navigate through the footer options  

to change the root password System configuration ---> Root password   

save the configuration by pressing [tab] and navigate to < Save > and press enter  
you would be prompted with a message that the configuration are saved to .config hit ok and press [esp] multiple time to exit 

start the build process by the following command 
```bash
make all
```
make process will take anywhere between 2 hrs to 4 hrs as the computational speed you have.

## flashing the output image

you may use your preferred  sdcard flashing tool like balena etcher, i will use the dd command for this 

```bash 
# find you memory block for the sd card attached from the following 
lsblk
#i got the output and found mine 16 gbs storage at sdb1 so i would be using that 
sudo dd if=output/images/sdcard.img of=/dev/sdb1
```

i have given link to the .img file for Raspberry Pi Zero W 2 board, you may directly use this one as well  

https://drive.google.com/file/d/1m-pO9T233HMS6A3zWerpMAsCeBeIbBQD/view?usp=sharing  

login:root  
password:12345678
