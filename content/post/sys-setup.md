
+++
title = "My system setup"
date = "2018-03-06"
hide_authorbox = false
disable_comments = false
categories = ["System"]
tags = ["Archlinux"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

How to set up my system

<!--more-->



### Micro Editor
Micro does not (yet) work with the termite terminal out of the box
To change the `TERM` variable in the shell add
```
export TERM=xterm-256color
```

### Termite
To create an initial config in Archlinux copy the standard one into `~/.config/termite`
```
mkdir ~/.config/termite
cp /etc/xdg/termite/config ~/.config/termite/config
```

### Fonts

Install Iosevka for terminal
```
trizen -S ttf-iosevka-term-ss04
```

The font name can then be found by listing all fonts `fc-list` and searching for elements of the name with `grep`. e.g.
```
fc-list | grep iosevka
```


### Pacman
Update archlinux mirror list
first fetchmirrors needs to be installed
```
 trizen -S fetchmirrors
```
Then run as root for in this case UK
```
sudo fetchmirrors -c GB
```

### i3

To get rid of the title bar on top of every window add this (at the end) of the `.~/.config/i3/config` file
```
new_window pixel 1
```
This leafes you with a small (blue) frame arounf the active window. If you want is to be more visible change the number to 2 or 3.
TO make the frame go away entirely use 0 or `new window none`

To switch from one workspace to the next with the `Win` plus `PageUp` / `PageDown` keys add this in the config file.
```
bindsym $mod+Next workspace next
bindsym $mod+Prior workspace prev
```

# System setup

Install AUR helper `trizen`

Chose a directory to install trizen [this can be removed after the installatioin? ]
```
git clone https://aur.archlinux.org/trizen.git
cd trizen
makepkg -si
```

### Add user to group

Check the assigned groups for a user with `groups`

To add a user to a group use this pattern
```
usermod -a -G group username
```

*Note:* The change is only effective after the next login.

*Give user access to Virtualbox shared folder*
```
sudo usermod -a -G vboxsf mmw
```
