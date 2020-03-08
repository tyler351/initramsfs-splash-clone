# Initramfs Splash
---

This is the next version of the initramfs still only a sample. The files contained with-in have no warrenty of any kind.

***Use at your own risk.***


## Boot Folder

initramfs.img - this is a custom built initramfs for the Raspberry Pi Single Board Computer it's purpose is
to enable a splash image at startup.  This is a universal initramfs it will work on all models.

## How To Use

Copy the initramfs.img to you boot folder and you also need to provide a splash image to display. This file
must be in PNG format and named splash.png.  Other restictions are the image resolution must be the same or
small than the screen at boot.  (This is a limitation of the image loading program.)

Edit your config.txt file and add the following line.

`initramfs initramfs.img`

## Tools

**edit_initramfs** : This script that will unpack the current initramfs stored it the boot folder to the tmp folder  
**pack_initramfs** : This script will pack the /tmp/initramfs folder into the initramfs.img in the boot folder  

## Todo

* [ ] - Add image resizing
* [ ] - Ability to select image
* [X] - Reduce size
* [ ] - Investigate if Busybox can be refined even more.

## Other Software used

* [BusyBox 1.31.1](busybox.net)
* fbsplash 0.4 *my own project*

## Updates

BusyBox 1.31.1 has been recompiled to be smaller, and has had many features removed. There still might be more that can be removed.

## BusyBox

In the config/busybox.config are the settings used to compile busybox used in this project. If you wish to compile busybox yourself you can use this config file as a base to add or remove features.  
**<u>/!\</u> WARNING <u>/!\\</u> :** *Removing some features has not been tested and may cause initramfs splash to fail.*

## Bugs





