
+++
title = "A QEMU Virtual machine with a Windows host and a Linux guest"
date = "2018-03-29"
hide_authorbox = false
disable_comments = false
categories = ["System"]
tags = ["Archlinux", "QEMU"]
aliases = ["/post/all-grown-up/"]
draft = false
+++

Run a (Arch)Linux system in a QEMU virtual machine on your Windows.

<!--more-->

# Intro

This is my first try to use QEMU to run Archlinux in a virtual machine.

To use a virtual machine like QEMU can be quite useful for various reasons.
- You cannot reinstall something else on you system. You need it as it is. So to install something new is not an option.
- You sometimes just want to try a new operating system without much risk that if anything goes wrong your current system takes damage.

If you have the choice between a system with 32 and 64 bit then choose the 64bit one. The newer 64bit processors have additional processor commands to support virtual machines. Sometimes these virtualization functions still have to be turned on in the BIOS.

When talking about virtual machines you find the expressions host and guest a lot.
- The **host** is the system that provides the virtual machine. In our case that is the Windows system.
- The **guest** is the operating system that runs in the virtual machine. In our case Archlinux.

Also to use QEMU you need to use the Windows command prompt. I haven't used it for 15 years, but what you need is really basic so you should be all right.

In this article I wan to set up a QEMU virtual machine with a Windows host and a Archlinux guest.

When the virtual machine is used I am looking for this kind of configuration:
- 2G of RAM memory
- 8 GB hard drive (enough for a test, for a system you use you might want more )
- 2 Processors
- 64MB Video Memory
- support for my native display resolution of 1366x768
- Network access
- shared drive between guest and host to exchange files
- shared clipboard between guest and host

Wifi setup is not for the guest Linux required even if you are actually using Wifi for you host computer. The virtual machine will make the network available to the guest as if it is a cable.

# Install QEMU on Windows

You can install QUEMU from their [website](https://www.qemu.org).
The installation is quite straight forward.

After the installation all QEMU commands are in the QEMU folder. However, at least in my case the folder has not been added to the Windows search path. That means the commands will not be found if you just type them into the command prompt.  

So instead of typing a `command` you have to be in the QEMU folder and then type `./command`

# Starting the virtual machine

Before you can start to install a new system you need a filesystem that the virtual machine can use and also a linux distribution ISO file.

## Create a virtual hard drive

To be able to install linux it has to has access to a hard drive. For a virtual machine the hard drive will be emulated by a file on Windows. There are two options for that file:
- **qcow2** : This format created a drive for linux that has exactly the size you specify on the linux guest side. However the Windows file that represents the hard drive will only grow to the size that is needed. So this option saves space but can also be bit slower.
- **raw** : The file uses exactly the size on your host Windows drive as you have specified. This option can be a bit quicker.

For this article we will use **qcow2**. You can create the drive wherever you want. I will put is in a sub-folder in QEMU named _harddrive_. The actually file is called _archlinux.hd_

Type this to create the harddrive:
```
./qemu-img create -f qcow2 harddrive\archlinux.hd 8G
```

## Download a linux distribution to install
First you need to download a linux ISO file somewhere. If you are not sure which one you want the [distrowatch](distrowatch.com) lists a lot of choices and ranks them by usage. Also some description is given and for some linux distros you can also find some reviews.

As the title said, for this article I will use Anarchy Linux. That is basically an installer helper to set up an Archlinux system without the hassle to do it all by hand. It's all driven by menus. Previously Anarchy Linux was also called ArchAnywhere. It is probably helpful if you have set up Archlinux by hand once, but not mandatory. Also some knowledge about using the shell is helpful for Archlinux. It is not difficult though and comes quite natural.

If in doubt maybe start with [Manjaro](https://manjaro.org/). That is a Archlinux based distro that is tailored for ease of use. It is quite popular, has decent documentation and you find a lot of help and forums in in the web.

Anarchy Linux can be found [here](https://anarchy-linux.org/)


## Run the virtual machine

So now that all preparations are done we can start the QEMU virtual machine. And install the Linux in the virtual hard drive.

```
qemu-system-x86_64 -m 2G -cdrom anarchy-cli-1.0.0-x86_64.iso -boot order=d -drive file=harddrive\archlinux.hd
```

- `m`: sets the memory available for the VM. Here 2GB, other options could be 512MB or whatever you want to give your Linux system.
- `-boot order=d` boot from cdrom rather than from hard drive.


To start and try your shiny new VM you can start it with
```
qemu-system-x86_64 -m 2G -boot order=c -drive file=harddrive\archlinux.hd
```

Aaand it turns out it is quite slow.

Luckily some things can be done.
1. Currently we use only one processor, So that can be increased to two.
2. QEMU needs some Intel libraries to support the hardware acceleration for modern AMD64 (aka X86_64) processors.

- To use 2 processors add the parameter `-smp 2` for 2 processors. That helps but not much.

The second option is to use the parameter `-accel hax`. There is a Intel package that needs to be present for this parameter to work.
Instructions [here](https://www.qemu.org/2017/11/22/haxm-usage-windows/)

The _-accel hax_ switch does seem to speed up things. Only problem so far is that my Linux installation crashes.
Well.

_to be continued, hopefully_
