# Re4son-Pi-TFT-Helper

A script for configuring TFT displays on a Raspberry Pi. This script is heavily based on Adafruit's PiTFT Helper.

This Helper is used in [Sticky Finger's Kali Pi](http://www.whitedome.com.au/kali-pi).

## TFT Documentation

Products:
The following products are fully supported:

- [PiTFT - Assembled 320x240 2.8" TFT+Touchscreen for Raspberry Pi](https://www.adafruit.com/product/1601)
- [PiTFT - Assembled 480x320 3.5" TFT+Touchscreen for Raspberry Pi](https://www.adafruit.com/product/2097)
- [Adafruit PiTFT 2.2" HAT Mini Kit - 320x240 2.2" TFT - No Touch](https://www.adafruit.com/product/2315)
- [Raspberry Pi 7" Touch Display - Rotate display 180 so power cable is at the top](https://www.raspberrypi.org/products/raspberry-pi-touch-display/)
- [Sainsmart 3.5"](http://www.sainsmart.com/sainsmart-3-5-inch-tft-lcd-320-480-touch-screen-display-for-raspberry-pi-2-b-b.html)
- [Waveshare 3.2"](http://www.waveshare.com/wiki/3.2inch_RPi_LCD_(B))
- [Waveshare 3.5"](http://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A))
- [Waveshare 5"](http://www.waveshare.com/wiki/5inch_HDMI_LCD)

The following products are not fully supported yet and need some manually configuration:
- Elecfreaks 2.2"
- [Hotmcu HY28B 2.8"](http://www.hotmcu.com/28-touch-screen-tft-lcd-with-all-interface-p-63.html)
- JBTek
- [Sainsmart 3.2"](http://www.sainsmart.com/sainsmart-3-2-tft-lcd-module-320-240-touch-screen-display-for-raspberry-pi.html)
- [Waveshare 4"](http://www.waveshare.com/wiki/4inch_RPi_LCD_(A))



## Getting Started: Kernel & Helper Script Installation

**Please be careful!** Installing a new kernel always has the potential to
leave your Raspberry Pi unbootable.  You should make a backup copy of your SD
card before trying this, or (even better!) start with a fresh card.

First, make sure /boot is mounted:
```sh
sudo mount | grep /boot
```
If /boot is not mounted, mount it now:
```sh
sudo mount /dev/mmcblk0p1 /boot
```

Install Sticky Finger's Kali-Pi Kernel:

```sh
cd ~
wget  http://whitedome.com.au/download/Kali-Pi-Kernels/re4son_kali-pi-tft_kernel_current.tar.gz
tar -xf re4son_kali-pi-tft_kernel_current.tar.gz
cd re4son_kali-pi-tft*
sudo ./install.sh
```
This can take a surprisingly long time to finish, especially if you're using a
slower SD card, so be patient.

Reboot.

This setup tool can be found in the root directory folder of the kernel package.
To update to the latest version, just run:

```sh
./re4son-pi-tft-setup -d
```

## Using Re4son-Pi-TFT-Helper

`re4son-pi-tft-helper` must be run with root privileges, and takes a parameter
specifying the type of TFT to configure.  Invoke it like so:

```sh
sudo re4son-pi-tft-helper -t 28r
```

For a full list of available options, check the help:

```sh
re4son-pi-tft-helper -h
```

## Updating Re4son-Pi-TFT-Helper

To reset all settings, just run:

```sh
mount /dev/mmcblk0p1 /boot
rm /boot/config.txt
rm /etc/X11/xorg.conf.d/99-fbdev.conf
rm /etc/X11/xorg.conf.d/99-calibration.conf
rm /etc/pointercal
rm /dev/input/touchscreen
```
