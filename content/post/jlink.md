+++
title = "Pinebook to PineTime connection with J-Link"
date = "2020-01-05"
hide_authorbox = false
disable_comments = false
categories = ["Embedded"]
tags = ["PineTime, J-Link"]
draft = true
+++

Using a J-Link EDU Mini to cenect from the PinebookPro to the Pinetime.

<!--more-->

# Intro

Check that the device is registered with `lsusb`. The J-Link  should be in this list. The name might not be your exact model.

It seems the Segger J-Link tools are not available for ARM Linux, only for x86. But luckily there is the [OpenOCD]() tool, and that comes for ARM Linux as well.


# OpenOCD


## Setup

Install the OpenOCD tool, e.g. on Manjaro ARM with `yay -S openocd`.

Once installed a udev rules must be copied to `/etc/udev/rules.d` if they are not already there.

The file is called something like `60-openocd.rules` and can be found with: `fine /usr -iname "openocd.rules"`. On Manjaro ARM the file was in `/usr/share/openocd/contrib/`

So to copy it over to /etc you can use these commands:
```
cd /usr/share/openocd/contrib/
sudo cp 60-openocd.rules /etc/udev/rules.d
```
Then reboot.


