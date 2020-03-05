# Initramfs Splash

This is just a sample upload for testing purposes. The files contained with-in have no warrenty of any kind.

Use at your own risk.


# Boot Folder

initramfs.img - this is a custom built initramfs for the Raspberry Pi Single Board Computer it's purpose is
to enable a splash image at startup.  This is a universal initramfs it will work on all models.

# How To Use

Copy the initramfs.img to you boot folder and you also need to provide a splash image to display. This file
must be in PNG format and named splash.png.  Other restictions are the image resolution must be the same or
small than the screen at boot.  (This is a limitation of the image loading program.)

Edit your config.txt file and add the following line.
`initramfs initramfs.img


# Todo

* [ ] - Add image resizing
* [ ] - Ability to select image
* [ ] - reduce size

# Other Software used

* BusyBox 1.31.1 

# Bugs





