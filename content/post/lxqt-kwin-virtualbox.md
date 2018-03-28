+++
title = "An Archlinux Desktop with LXQt and KWin"
date = "2017-12-03"
hide_authorbox = false
disable_comments = false
categories = ["Desktop Environments"]
tags = ["Linux","Archlinux","LXQt","KWin"]
aliases = ["/post/all-grown-up/"]
draft = false
+++


Setting up LXQt with KWin in Virtualbox using Anarchy Linux

<!--more-->


#KWin and LXQt and VirtualBox

This guide describes how to set up KWin and LXQt in Virtualbox using Arch Anywhere.

The basic setup should work with any Computer, Virtualbox is just what I use.

I have tried to install a relative light version with only a small memory footprint. There might be a more elegant solution though. If someone has an idea, please let me know.

## Setup VirtualBox
-  2 cores
* 2 GB ram (If you can spare that, 1GB also works, I hav not tested with less)
* Chipset: ICH9
* 3D acceleration on ?
* bi-directional copy and paste
* Display mem 64MB
* Shared folder (this is nice to have, later I will show how to set up the share)

## Run Arch Anywhere

Start Arch Anywhere. I have chosen the following setup. Feel free to change.

* no Wifi: network comes from the host-pc of VirtualBox.
* no swap partition (a swap file can be set up later if required, I don't have one)
* Accept virtualbox-guest-additions

### Additional apps
* VLC: I have chosen that for video

## Install
1. choose LXQT as desktop environment
2. Reboot

## After the first boot
1. login as root
2. Create a user  in the terminal
> `useradd -m -G users,wheel,audio  archuser`
>
>`passwd archuser`

3.  Update the system
> `sudo pacman -Syu`

4. Install Kwin
> `sudo pacman -S kwin`

5. Instal Kwin system setting dialog
This enanbles the Kwin setting dialog. You can access the setting by clicking in the upper left menu of a window. There you see *more actions* and in that menu you see
> `sudo pacman -S kde-cli-tools`

6. Kwin-Gtk compability
To change the theme of GTK apps in LXQt you need the LXDE appearance app. It has almost no dependencies, so it does not add much.
> `sudo pacman -S lxappearance`
In the lxappearance app you can chose the theme the gtk apps use.
To see gtk apps with the Kwin Breeze themes add
> `sudo pacman -S breeze-gtk`

7.  Fine tuning
In my installation I had trouble with changing apps using Alt-Tab. Looking into the logs it turned out an app called `kglobalaccel5` was not running. I have no idea where this app should be started but adding it to the LXQt autostart did it for me.
> add to LXQt autostart:
`Menu -> Preferences -> LXQT settings -> Session Settings`
> In tab Autostart add kglobalaccel5 to LXQT Autostart

 ( If you still have trouble check the  Kwin settings in tab `Task switcher`.  The flag `current activity` has to be set to on )


## Install additional software

This is a selection of mostly Qt software that I found usefull.

### Browser
I have chosen Qupzilla. Serves me well and is relativlely light.
> `sudo pacman -S qupzilla`

ALternative:
> `sudo pacman -S firefox`

###AUR repository
To use packages from the AUR repository it is very helpful to use a package managemr for AUR. Pacman does not cover AUR packages. There are many options but I like trizen the best. It works like pacman with some additional functions for AUR packages.

```
git clone https://aur.archlinux.org/trizen.git
cd trizen
makepkg -si
```

You can basically replace your use of pacman with trizen. Only for some special cases you can still use pacman.

### Graphical Editor: howl
Install howl ( gui editor) from AUR repository
> `trizen -S howl`

You don't need to use sudo for trizen, you will be asked for the sudo passwd later

### Image viewer: LX-Image
Install lximage package from AUR repository
> `trizen -S lximage-qt`

### PDF viewer: qPDFview
> `trizen -S qpdfview`


### Disk space checker: QDirStat
> `trizen -S qdirstat`

### Terminal: LX Terminal
Many LXQt editions use Qterminal. I like it but some keys are not accessible from programms in the console. So I use LX Termianl which has hardly any dependencies and is a bit smoother in my view.

> `sudo pacman -S lxterminal`

### Console Editor Micro
Install Micro from the AUR repository:

> `trizen -S micro-bin`

### Alternative: Console Editor: Tilde
Install Tilde (console editor)  from AUR repository
Tilde is a very user friendly console text editor that uses mostly the same keybindings as graphical apps like Ctrl-C for copy, Ctrl-V for paste and so on and comes with the menu (Alt-f for the file-menu for example)

This package requires the packages `fakeroot` and  `pkg_config`.  Install these packages before you install tilde

> `trizen -S tilde`

When you install Tilde several libraries will be installed during the process as dependencies. Most called ligt3*, etc.

### Download the arch-anywhere tool fetchmirrors

> `trizen -S fetchmirrors`

Use this tool to set up the right mirror servers for the Arch repository

`fetchmirrors --help` for help

## trizen PGP Tip

If you face a PGP authentication issue using trizen check this:

Error message during trizen build is:
`ERROR: One or more PGP signatures could not be verified!`
:

If you trust the package copy the public `KEYID` from the error message
Then use these commands in the console to add the new key:


> gpg --recv-key `KEYID`
> gpg --lsign `KEYID`


For details how that works [read:](http://allanmcrae.com/2015/01/two-pgp-keyrings-for-package-management-in-arch-linux/)

Helpful hints, comments and questions are welcome
