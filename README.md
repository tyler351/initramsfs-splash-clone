# Initramfs Splash

An extremely simple to use Initramfs based boot splash targeted towards the Raspberry Pi computer line.  


The files contained with-in have no warranty of any kind.

***Use at your own risk.***

WARNING This is not yet compatible with NETBOOT OR MSD BOOTING!! Support will be coming!

Not compatible with overlayfs from raspi-config out of the box see [OVERLAYFS.md](OVERLAYFS.md "Workaround available")


## * **IMPORTANT NOTICE** *  
Recent changes in the kernel require an update to the initramfs.img simply pull the changes and replace your initramfs.img with the new version. Please be aware that there was a bug in fbsplash and if you use this utility outside the initramfs.img you will need to update it as well the current version is now 0.7.

## Quick Start Guide

To get up and running is very simple!!
you need to add this line to the /boot/config.txt
```
initramfs initramfs.img
```
Next you need to add the following to you /boot/cmdline.txt
```
logo.nologo loglevel=0 splash silent quiet
```
*IMPORTANT* This must be all on one line   
Next you need the image you want to display this can be a PNG,JPEG, or BMP copy it to the /boot and edit /boot/splash.txt
```
## Initramfs-Splash
image=splash.png
fullscreen=0
```
*IMPORTANT* replace splash.png with your image
and finally copy the initramfs.img to your /boot

Reboot

## Boot Folder

initramfs.img - this is a custom built initramfs for the Raspberry Pi Single Board Computer it's purpose is
to enable a splash image at start-up.  This is a universal initramfs it will work on all models.

## Splash configuration

It's now possible to set the name of the splash image. I've added the ability to read a configuration file from the boot folder named splash.txt.  
**current settings**  
image=*imagename*  #imagename can be a jpg, png, or bmp the image must be stored in boot  
fullscreen=*[0|1]*  #Show image full screen. 0 = regular size, 1 full screen maintains aspect ratio.  
stretch=*[0|1]*   #Show image full screen and stretch it to fit the display. 
  
## Tools

**edit_initramfs**   : This script that will unpack the current initramfs stored it the boot folder to the tmp folder  
**pack_initramfs**   : This script will pack the /tmp/initramfs folder into the initramfs.img in the boot folder  
**create_initramfs** : This script will create a new root layout for the initramfs  

## Todo

* [X] - Add image resizing
* [X] - Ability to select image
* [X] - Reduce size
* [X] - Investigate if Busybox can be refined even more.
* [ ] - Workaround for Pi 4B with vc-fkms-v3d
* [ ] - Automate install

## Other Software used

* [BusyBox 1.31.1](https://www.busybox.net/)
* fbsplash 0.7 *my own project*

## Updates

fbsplash 0.7 Version update. Correct a bug that clears the screen immeditely after exit, this bug is due to recent changes to the Kernel.   
BusyBox 1.31.1 has been recompiled to be smaller, and has had many features removed. There still might be more that can be removed.

## BusyBox

In the config/busybox.config are the settings used to compile busybox used in this project. If you wish to compile busybox yourself you can use this config file as a base to add or remove features.  
**/!\\ WARNING /!\\ :** *Removing some features has not been tested and may cause initramfs splash to fail.*

## FBSplash

FBSplash is my own image loader it has been updated to version 0.5 this has solved the issue of images that are too large for the display crashing.  If an image is too large it will now be scaled to fit the screen and maintain it's aspect ratio.  
FBSplash version 0.6 is now included and adds the option to use free aspect this will allow for image stretching. 

## Bugs

* It isn't a BUG as much as a limitation with Pi 4B and the **vc-fkms-v3d** driver enabled. This causes the screen to blank and the splash to remain on screen for a short time.  This is caused be the driver it must reset the display.  I will be including a service that will bring the splash back after the reset.




