
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

### Atom editor
- Comand palette remembers last word
- set totally fabulous East End syntax/ui theme
- remove RET from autocomplete-plus (set in settings menu)
- set ctrl-space for command pallete
- set alt-pageup/down to swith between left an right pane
- TODO: check keymap settings to

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

## nodejs and npm
Install npm and nodejs with
```
trizen -S nodejs
```

In most of my attempts npm did not work well. Installing locally gave no result and installing globally failed with an error:
> npm ERR! Error: EACCES: permission denied, access '/usr/lib/node_modules

So this is the [suggestion](https://docs.npmjs.com/getting-started/fixing-npm-permissions) you can find in the npm manual.

1. Make a directory for global installations:
```
 mkdir ~/.npm-global
```
2. Configure npm to use the new directory path:
```
 npm config set prefix '~/.npm-global'
```
3. Open or create a ~/.profile (or .bash_profile, or whatever it is on your system) file and add this line:
```
 export PATH=~/.npm-global/bin:$PATH
```
5. Back on the command line, update your system variables:
```
6.  source ~/.profile
```

# System setup

Install AUR helper `trizen`

Chose a directory to install trizen [this can be removed after the installation? ]
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

### Change (bash) shell to fish.
This describes how to make fish your default shell.
Fist install the fish shell.
```
trizen -S fish
```

Find the documentation [here](https://fishshell.com/docs/current/tutorial.html#tut_learning_Fish)

To make fish your default shell you need to find out it's path with `whereis fish`. Most likely it's `/usr/bin/fish`.

Once you have the path to fish use the command `chsh` (change shell) to make fish the default shell.
```
chsh -s /usr/bin/fish
```
Instead of using setting varialbles (and this includes the $PATH) in .bashrc or .profile or so in fish you use the `set` command.
So with `set TERM xterm-256color` you add a variable.
