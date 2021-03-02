# Using LXQt with the Manjaro ARM KDE version.
(28/11/2020)

This text is written with the PinebookPro (PBP) in mind, but I guess almost all of it will work with Manjaro ARM and LXQt in general. Also, not all settings described here are neccessary. Pick and mix.

The KDE desktop environment works very well on the PinebookPro. 
However in comparison to LXQT as desktop environment it still feels that small moment slower. (e.g. startup) and uses more memory.

So, my idea is to use LXQt together with the PinebookPro KDE edition and to use KWin as window manager for LXQt.

This text is based on LXQt 16.

## LXQt install
Not much is necessary for a  working LXQt version if you have KDE already.

Install these packages:
- lxqt
- nm-tray-git
- libstatgrab (optional)
- libsysstat (optional)
- kvantum-qt5
- mcmojave-circle-icon-theme-git (optional)

**nm-tray-git** nm-tray is required if you want an icon in the panel to show the wifi network status. An alternative for the terminal is 'nmtui'

**libstatgrab** to use the SysInfo widget in the panel.

**libsysstat**  to use the SysStats widget in the panel.

**kvantum-qt5** is a great tool to change the appearance of LXQt (or any Qt environment incl. KDE)

**mcmojave-circle-icon-theme-git** A nice icon theme that shows all icons in LXQt

After the install you need to logout and change the desktop environment in the desktop manager to LXQt desktop and then log in again.

### Mouse Settings

Manjaro uses the Synaptic mouse/touchpad driver. Some of the setting is done from Plasma though and LXQt only supports libinput mouse/touchpads, so the touchpad is not set up so great aftet the first start. This is the one thing that needs a bit of tuning. This means that TabClick is not turned on and you have to actually physically click the touchpad down to click somewhere until you fix it.

The solutions is to add a config file in `/etc/X11/xorg.conf.d` as  described in the [Wiki](https://wiki.pine64.org/wiki/Pinebook_Pro#X-Windows_.26_trackpad_settings)

As a quick fix these commands in '.bash_profile' or even just keyed in the terminal does it.
```
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=2
```

While running Plasma just key in `synclient` to see what Plasma uses and replicate what you like in the config file.

## Use KWIN as window manager.

The standard OpenBox window manager does not use OpenGL and graphics acceleration but KWin does and it works super with LXQt.
There are some implications though. Window management related setting would still happen in the KDE setting and not the LXQt settings. e.g. keyboard shortcuts, 

To change the window manager for LXQt to Kwin go to:
Preferences -> LXQt Settings -> Session Settings -> Basic Settings -> Window Manager

![lxqt-session-settings|458x500](upload://fbtyKWwSJsa9T3RT6bxyxnxkvqq.png) 

Change the window manager to `kwin_x11`.


## Kvantum and appearance

Kvantum (`kvantum-qt5`) is the Swiss army knife of desktop decoration for LXQt. 
It comes with a list of pre-installed themes and it's own configuration dialog in LXQt settings to choose the theme.

To use a Kvantum theme choose on in:
1. `LXQt settings` -> `Kvantum Manager` -> `Change/Delete Theme` -> `Select a theme`

If you want to use Kvantum you need to make some additional changes to the LXQt settings to make the most of it:

2. `LXQt settings` -> `Appearance` -> `LXQt Theme`: Kvantum
3. `LXQt settings` -> `Appearance` -> `Widget Style` -> `Qt-Style`: kvantum(-dark)

- Setting a theme in the Kvantum settings dialogue changes mostly the look and feel of window content, like buttons and so on and the LXQt panel and so on.
- The one thing that unfortunately still is controlled by KWin and its setting is the window title bar. To change that style you have to use KDE system settings, which works fine in LXQt.

More info to Kvantum and how to create your own themes [here](https://github.com/tsujan/Kvantum/tree/master/Kvantum) in the `doc` folder and the README.

![lxqt-desktop|690x388](upload://vQCZPtbCp1eZlJuksWTc5cCmzYR.png) 

## Panel on left side of screen

They idea is that a laptop screen is quite wide but in comparison not very high, so moving the panel to the left increases the height available for apps

1. Move Panel to left
- right click on the panel
- `configure panel` -> `position`: Left of Desktop

2. If you move the Panel to the left (or right) of the screen, you have to do a few optical adjustments to make it work nicely.

- right click on the panel
- `Panel` -> `configure panel` -> `Size`: 55   (to make the panel a bit wider)
- `Panel` -> `configure panel` -> `Icon Size`: 32  (to adjust for the wider Panel)
- `Widgets` -> `Task manager` -> `Settings` -> `Button Style`: Icons only  (there is no space for the text)
- `Widgets` -> `Task manager` -> `Settings` -> `Maximum Button Height`: 65   (to allow for more icons in the Task manager)
- `Widgets` -> `World clock` -> `Settings` -> `General` -> `Autorotate ..`: Uncheck 

![lxqt-panel-config|362x500](upload://8doiHwGHbQAm7ZIDYLKPdTkMuvf.png) 

## Icon set
The default  icon set works ok-ish for LXQt but you might want to be able to choose some other options. 

Here KDE comes in handy, in the KDE Settings for Icons you get an `Get new Icons` dialogue with a long list of options that you can install and you can also preview the icon sets. 
If you install an icon set with KDE you can then also use it with LXQt. 

As an alternative for many icon sets an AUR package exists. e.g. McMojave circle icons: `mcmojave-circle-icon-theme-git`.

![lxqt-config|514x500](upload://jXZzNNqJSKZd5YQaSnzUHXpuIVJ.png) 

Please note that you can also set an icon set for the `Application Menu` separately in it's settings.

And last but not lest if you are not quite happy with the battery icon you can change that in the `LXQT Settings` -> `Power management Settings` -> `use icon from theme`.



## Wallpaper and font

### Set a wallpaper
- right click anywhere on the Desktop
- `Desktop Preferences` -> `Wallpaper image file`: choose wallpaper

For new open source wallpapers you can search at e.g. [Pexels](https://www.pexels.com/). 
For the Pinebook(Pro) use the size 1920 x 1080.

### Change Font size TODO:check if really relevant

- open LXQt Settings. 
- `Appearance` -> `Font` -> `Point Size`: 12
- `Appearance` -> `Font` -> `Resolution (DPI)`: 120
- `Openbox Settings` -> `Font`: +1 of current size

- right click Panel
- `Manage Widgets` -> `Application Menu` -> `Settings` -> `Custom Font size`: 14

## Settings mix

Not unsimilar to Openbox the settings related to the window manager (here Kwin) are managed by, well the window manager or in this case KDE Plasma.

That means things that Kwin controls, like window effects or keyboard shortcuts  have to be set up with 'KDE system settings'. This has been installed with Plasma anyway and can be used in LXQt to change settings without problems.

Settings that are done in `KDE system settings`:
- **Virtual desktops**:  KDE -> Workspace behaviour - > Virtual Desktops 
- **Window decoration**: KDE -> Settings -> Application Stype -> Window decorations
- **Shortcuts**: KDE -> Settings -> Shortcuts
- **Desktop Effects**: KDE -> Workspace behaviour -> Desktop Effects

Keyboard shortcuts, again in a similar way as with Openbox work like this: If a shortcut is defined in KDE system settings then Kwin will capture it and try to execute it. 
If the shortcut is directly for
 Kwin that works fine. If another KDE Plasma app should execute the shortcut then that bit of Plasma is not started and the shortcut effectively does nothing.

All other shortcuts that are not defined in KDE system settings are handed to LXQt next and can be used in there.

As a consequence of this it might be advisable to run through 'KDE system settings' and 'LXQt configuration' in a quiet moment and turn off all unneeded shortcuts. 

## More Virtual Desktops

The display of the PBP is great, but like with any laptop it has only so much space and after a while a lot of windows overlap each other.

It can be  practical to use more than one virtual desktop. This means that one program runs on one desktop and another on a different one and you can easily flip between them.

This avoids that many windows overlap each other. If shortcuts are set up to switch between desktops that can be a swift experience, however the mouse is also supported.

To set up 4 virtual desktops in total: 

`KDE system setting` -> `Workspace behaviour` -> `Virtual Desktops`: 'Add' 3 more desktops.

![kde-virtual-desktop|690x314](upload://4IX9dYOUslNtwEvkaHxgLKkkTNd.png) 

To show the 4 desktops nicely in the panel right click the panel: 
- `Manage widgets` -> `Desktop switcher` -> `Number of rows`: 4

It can be usefull to use the same apps on the same virtual desktops all the time. 
That way you always have a clear idea where they are.  For myself I use this pattern (mostly)

- Desptop 1: For the terminal and settings and system tasks 
- Desptop 2: For the browser
- Desptop 3: Editors or generally for writing
- Desptop 4: Other stuff as it comes

This whole procedure is a bit borrowed from tiling window managers.

## Notifications

A small  thing is to set the time System notifications are shown. Default is 10 sec.

- `LXQt settings` -> `Desktop notifications` -> `Advanced settings` -> `Default duration`: 3 sec

## Session Settings

- add Firefox and your preferred  terminal to `Default Applications`
- `Basic Settings` ->  `Leave session` -> `Ask for confirmation..`: un-tick   (if you don't want to confirm that when you logout or shut down)

## Change CAPSLOCK to Menu

If you like me have no real use for the CapsLock key then one nice usage is to map the MENU key function to it.
This will basically make the CapsLock key behave as if you have pressed the right mouse button to get the context menu.

e.g. this is quite helpful for the auto-correct function in the browser, if you write for example in a forum you can get the auto-correct suggestions buy moving the cursor to a misspelled word and pressing CapsLock for the context menu instead of doing that with the mouse.

```
setxkbmap -option caps:menu
```

Add this line to your `.bash_profile` (There might be a better place for this but it works)

## Display brightness keybindings

Kwin captures all keyboard-shortcuts that are defined in `KDE system Settings` for brightness (Fn + F1/F2). For the brightness settings in LXQt you have to add different keyboard settings in LXQt than in Plasma. Maybe `Ctrl-Shift + F1/F2`

The commands are:
```
lxqt-backlight_backend --inc
lxqt-backlight_backend --dec
```
to increase of decrease the brightness

## Activate items per single click.

Originally many GUIs use  a double click on an icon to initiate an action.  It is also possible to activate icons with a single click.

In LXQt there are several settings to activate single click consistently.

- `LXQt Settings` -> `Appearance` -> `Widget Style` -> `Activate item on single click`: tic

- `LXQt Settings` -> `Mouse and Keyboard` -> `Mouse` -> `Activate item on single click`: tic

- `PCManFM FileManager` -> `Edit` -> `Preferences` -> `Behaviour` -> `Open files on single click`: tic

## Ensure wifi password is saved
If your Wifi password does not get saved when you connect to a new network try this..

Add a policy to the /etc folder like this:

Add this file,  use sudo
```
/etc/polkit-1/rules.d/50-org.freedesktop.NetworkManager.rules
```

e.g. if your editor is micro:

```
sudo micro /etc/polkit-1/rules.d/50-org.freedesktop.NetworkManager.rules
```

Then copy these lines into editor and save with Ctrl+s, leave the editor with Ctrl+q.
```
polkit.addRule(function(action, subject) {
  if (action.id.indexOf("org.freedesktop.NetworkManager.") == 0 && subject.isInGroup("network")) {
    return polkit.Result.YES;
  }
});
```

See:
[Archlinux Wiki Network Manager](https://wiki.archlinux.org/index.php/NetworkManager)

## Save git passwords

If you use `git` and want to avoid to key in your repro passwords all the time you can use 'lxqt-openssh-askpass' or alternatively `ksshaskpass`.

Add these values in LXQt Config -> Session Settings -> Environment

```
GIT_ASKPASS='/usr/bin/lxqt- and the [README](https://github.com/lxqt/lxqt-openssh-askpass)
```
(or /usr/bin/ksshaskpass)

For more details and a solution for SSH keys. Check [here in the Archlinux Wiki](https://wiki.archlinux.org/index.php/KDE_Wallet#Using_the_KDE_Wallet_to_store_ssh_key_passphrases)

You can also add a le like this to `.bash_profile`
```
export GIT_ASKPASS='/usr/bin/ksshaskpass'
```	

There is a bit of a discussion going on in the LXQt team wheather to use `lxqt-openssh-askpass` or `ksshakspass`, but for now (Nov 2020) the LXQt solution is still the supported one.

[See this issue](https://github.com/lxqt/lxqt/issues/362) and the [README](https://github.com/lxqt/lxqt-openssh-askpass)

## Nextcloud auto login

If you are using nextcloud-client to sync your Nextcloud storage and you find that the nextcloud-client does not access the Kwallet correctly. Try this..

Install `gnome-keyring`. That works.

## Bluetooth

There is no direct bluetooth support in LXQt but this works:

To get bluetooth working I installed these packages and used `bluetoothctl` to set it up for an external keyboard and loudspeaker. Works but the setup took a moment. 
- bluez-utils
- pulseaudio-bluetooth
- blueman

This [guide in the Archlinux Wiki](https://wiki.archlinux.org/index.php/Bluetooth#Pairing) was helpful.

### bluetoothctl

Here are roughly the steps to pair a Bluetooth device. Also read the docu.

These are the steps, a bit frickely
- power on
- scan on
- devices
- info B8 - Sony (example)
- connect

### Blueman
`blueman` is a GTK3 front-end to set up and manage bluetooth and it works

## Done

That's all. With this you should be able to set up LXQt in the way it works for you.

![lxqt-desktop2|690x388](upload://zieHoJvGHc7Hi7JDaUGth4SjE5t.png) 
