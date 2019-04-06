+++
title = "LXQt and KWin"
date = "2019-02-20"
hide_authorbox = false
disable_comments = false
categories = ["Desktop Environments"]
tags = ["Linux","LXQt","KWin"]
aliases = ["/post/all-grown-up/"]
draft = true
+++


Setting up LXQt with KWin

<!--more-->


#KWin and LXQt and VirtualBox

This guide describes how to set up KWin and LXQt.

I have tried to install a relative light version with only a small memory footprint of KWin. There might be a more elegant solution though. If someone has an idea, please let me know.

## Install
1. choose LXQT as desktop environment

4. Install Kwin
> `sudo pacman -S kwin`

5. Install Kwin system setting dialog
This enanbles the Kwin setting dialog. You can access the setting by clicking in the upper left menu of a window. There you see *more actions* and in that menu you see
> `sudo pacman -S kde-cli-tools`

The kwin settings tool is `kcmshell5`

Unfortuntely in the oment (Feb 2019) kcmshell5 requires libkworkspace.so which is in plasma-workspace only and so you get the whole kde-plasma installation anyway.

In that case you can also install `systemsettings`,  the kde-settings.




Thetool to start the seuop is called kcmshell5

6. Kwin-Gtk compatibility -> is this still needed ?
To change the theme of GTK apps in LXQt you need the LXDE appearance app. It has almost no dependencies, so it does not add much.
> `sudo pacman -S lxappearance`
In the lxappearance app you can chose the theme the gtk apps use.
	
7. To see gtk apps with the Kwin Breeze themes add
> `sudo pacman -S breeze-gtk`

##  Fine tuning
In my installation I had trouble with changing apps using Alt-Tab. Looking into the logs it turned out an app called `kglobalaccel5` was not running. I have no idea where this app should be started but adding it to the LXQt autostart did it for me.
> add to LXQt autostart:
`Menu -> Preferences -> LXQT settings -> Session Settings`
> In tab Autostart add kglobalaccel5 to LXQT Autostart

 ( If you still have trouble check the  Kwin settings in tab `Task switcher`.  The flag `current activity` has to be set to on )

# Kwin - Openbox comparison

- Kwin has compositing build in
- Improved vsync
- startup size on my system (checked in htop) :

| Wm | Size |
| ---| ---  |
| Kwin | 353M |
| Openbox | 289 |

This is for a quite raw Kwin installation, maybe something could be optimized.

## Install additional software

Here is an extensive list of programmes that work well with Qt5

[](https://wiki.manjaro.org/index.php?title=List_of_Qt_Applications)