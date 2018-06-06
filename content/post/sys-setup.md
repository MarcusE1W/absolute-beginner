
+++
title = "My system setup"
date = "2018-04-28"
hide_authorbox = false
disable_comments = false
categories = ["System"]
tags = ["Archlinux", "Spectrwm", "Micro editor", "trizen", "Fish shell", "Atom"]
draft = false
+++

These are my notes to remember how to set up my system.

<!--more-->

# Set up programms

This whole article is probably only useful to myself, unless you use Archlinux and similar programms as me, in which case you are welcome to have a look how I try to set mine up.

## Micro Editor
Micro does not (yet) work with the termite terminal out of the box
To change the `TERM` variable in the shell add to .bash_profile or whatever the equivalent in your shell
```
export TERM=xterm-256color
```

To have copy and paste working with all other X11 apps install `xclip`
```
trizen -S xclip
```
This is an optional dependency of micro but is really very useful.

To enable the use of arrow keys in the Linux console (no GUI) follow these [instructions](https://github.com/zyedidia/micro/wiki/Linux-Console-Keybindings)


## Atom editor
- Comand palette remembers last word -> settings edior
- set absolutely fabulous East End notebook syntax/ui theme
- remove RET from autocomplete-plus (set in settings menu)
- set ctrl-space for command pallete
- set alt-pageup/down to swith between left an right pane
- TODO: check keymap settings to

## Termite
To create an initial config in Archlinux copy the standard one into `~/.config/termite`
```
mkdir ~/.config/termite
cp /etc/xdg/termite/config ~/.config/termite/config
```

## Fonts

Install Iosevka for terminal
```
trizen -S ttf-iosevka-term-ss04
```

The font name can then be found by listing all fonts `fc-list` and searching for elements of the name with `grep`. e.g.
```
fc-list | grep iosevka
```


## Pacman


To use the most responsive archlinux mirror in your area update the archlinux mirror list
- first fetchmirrors needs to be installed
```
 trizen -S fetchmirrors
```
- Then run as root, in this case for UK
```
sudo fetchmirrors -c GB
```
Allow to update your mirror list

### Useful commands for pacman

These commands usually also work with a pacman helper like trizen.

- List explicitly installed packages
```
sudo pacman -Qqe
```

- that are not also a dependency for other packages.
```
sudo pacman -Qent
```

- List all _foreign_ packages. That means from AUR or manually installed.
```
pacman -Qn
```

- List all installed files for a package
```
sudo pacman -Ql package_name
```

- List all packages that have been installed as dependency to another package
```
sudo pacman -Qd
```

- List all packages no longer required as dependencies (orphans):
```
sudo pacman -Qdt
```


## i3

To get rid of the title bar on top of every window add this (at the end) of the `.~/.config/i3/config` file
```
new_window pixel 1
```
This leafes you with a small (blue) frame around the active window. If you want it to be more visible change the number to 2 or 3.
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

## Add user to group

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

?? seems not to work ...

## Change (bash) shell to fish.
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

I tink to export the variable you add  `-x`

### Aliases and functions in fish

To see all defined functions you can use the `functions` comand. NOte the plural.

To see the definition of a specific function add the name after the command e.g. `functions ll`

Aliases are nothing else but functions in fish. Functions are described in the tutuorial. however, there is a convenient shortcut to define a functionin the form of the alias command. Not unsimilar to bash.

With `alias la "ls -a"` you can define a alias/function for la.

With `functions la` you can see how the functions definition you just created looks like.

If you want to save the functions to make it permanent use "funcsave la"

## spectrwm tiling window manager
Install with
```
trizen -S spectrwm
```
For a first overview the man pages are usefull: `man spectrwm`

For more [XDG](https://www.freedesktop.org/wiki/Software/xdg-utils/) integration you could install `xdg-utils`.

### First Configuration
spectrwm looks in ~/.spectrwm first and then for /etc/spectrwm.conf
So if you do not have config file in your home folder yet, copy it from /etc
```
cp /etc/spectrwm.conf ~/.spectrwm.conf
```
For Archlinux the standard `bar_font` paramenter needs to be updated as described in the [Wiki](...)

To change keybindings you can copy one of the predefined keyboard mappings in folder `/etc/spectrwm`

To copy e.g. the us keyboard layout into your .config forlder type:
```
mkdir ~/.config/spectrwm
cp cp /etc/spectrwm/spectrwm_us.conf ~/.config/spectrwm/spectrwm_us.conf
```
To point spectrwm to your new keymapping file you need to update the .spectrwm.conf file.

Update keyboard_mapping like this:
```
# This allows you to include pre-defined key bindings for your keyboard layout.
keyboard_mapping = ~/.config/spectrwm/.spectrwm_us.conf
```

Last but not least, change your .xinitrc
```
exec spectrwm
```
### Spectrwm keymap configuration

I have found the following keybindings helpful:
```
bind[focus_next]	= MOD+Right      # Move to next programme on the same workspace
bind[focus_prev]	= MOD+Left
bind[term]		    = MOD+Return     # Start a terminal
bind[ws_next]	    = MOD+Next
bind[ws_prev]	    = MOD+Prior
```

If you use Linux in a Virtual machine on Windows like me then you will find that Win+l is permanently used by Windows to lock the screen. Even if you use VirtualBox. That means MOD+l to grow the master window will also trigger the screen lock. I just use the  key next to `l` to grow the master window. In my case ;

For Spectrwm you have to use xkb xharacter names. You can find the name of a character with the tool `xev`. The output is a bit messy and for ; looks like this:

> KeyPress event, serial 37, synthetic NO, window 0x1600001,
>
>    root 0x2bd, subw 0x0, time 64418407, (590,691), root:(1265,692),
>
>    state 0x0, keycode 47 (keysym 0x3b, **semicolon**), same_screen YES,
>
>    XLookupString gives 1 bytes: (3b) ";"
>
>    XmbLookupString gives 1 bytes: (3b) ";"
>
>    XFilterEvent returns: False

So the xkb keycode for ; is - tada **semicolon**

So to bind the master_grow command to MOD+; you have to add this line to the keymap file.
```
bind[master_grow]	= MOD+semicolon  # Make current window smaller.
```
### Setup for screenshots

To make the screenshot function work you have to
- copy screenshot.sh from /usr/share/spectrwm to ~/local/bin (or any other place that is in your local PATH)
- make sure the screenshot tool `scrot` is installed
- change the config and if you want keymapping
