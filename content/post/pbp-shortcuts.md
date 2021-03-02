# Using LXQt with the Manjaro ARM KDE version.

This text is written with the Pinebook Pro (PBP) in mind, but I guess almost all of it will work with Manjaro ARM and LXQt in general._

The KDE desktop environment works surprisingly well on the original (OG) Pinebook and very well on the PinebookPro. 
However in comparison to LXQT as desktop environment it still feels that small moment slower. 
Also  LXQt uses less memory. Memory is always good to have, especially on the OG Pinebook where it makes the difference between Firefox browsing works fine (LXQt) in most circumstances to the system occasionally freezes (KDE), not quite sure why, but it looks like the system runs out of memory.

So, my idea is to use LXQt together with the Pinebook (Pro) KDE edition. 
This adds just about 30 MB to your drive as some of the dependencies come with KDE anyway. It also opens the opportunity to use Kwin as window manager in LXQt.

Here I will describe the basic installation, some nice additions and then how I set it up for myself. 
Obviously taste is very different and some might like it in another way, however it might help to find what is the right setup for you. 
The idea is also to use KDE functions if there is no LXQt equivalent as they are available anyway. e.g. kwallet

If someone has different or additional solutions to make LXQt run smoothly I would also love to hear about them.

## Minimum LXQt install
Not much is necessary for a minimum working LXQt version if you have KDE already.

Install these packages:
- lxqt
- nm-tray-git

nm-tray is required if you want an icon in the panel to show the wifi network status.

## Compfy LXQT install

Install:
- xorg-xinput
- libstatgrab
- libsysstat
- kvantum-qt5
- ksshaskpass
- mcmojave-circle-icon-theme-git

**xinput** can be used to set up the mouse/trackpad settings.

**libstatgrab** is required to use the SysInfo widget in the panel.

**libsysstat** is required to use the SysStats widget in the panel.

**kvantum-qt5** is a great tool to change the appearance of LXQt (or any Qt environment incl. KDE)

**ksshaskpass** This is not strictly related to LXQt but works nicely to store your git passwords in kwallet (which comes with KDE)

**mcmojave-circle-icon-theme-git** A nice icon theme that shows all icons in LXQt

## Use KWIN as window manager.



## Added functions

Here is a list of settings to ensure a smooth functional LXQt desktop

### Mouse Settings

```
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=2
```

XXX See the PBP wiki for more details


### Ensure wifi password is saved

When using KDE the Wifi password get's saved as expected in kwallet, however for some reason this does not happen when using LXQt.
So the solution is to add a policy to the /etc folder like this:

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


### Keyboard shortcuts

The trackpad for the OG Pinebook is not so great, so I got into the habit of using keyboard shortcuts more. 

The general idea is: 

**Meta key**:   for the desktop environment and LXQt
**Ctrl key:**   for programme standard shortcuts (this is depending on the actual app)
**Alt key**:    for personal self defined shortcuts in a programme

This means we set the shortcuts for LXQt up with the Meta key. That's the Pine key on the PinebookPro and the Line Key on the OG Pinebook.

For LXQt there are two places where shortcuts are defined. The first is the LXQT Shortcut Keys settings. Here are mostly settings concerning the environment and to start programmes.

All settings concerning window management are done by Openbox, the standard window manager of LXQt. And Openbox supports some cool window manager shortcuts.

#### LXQt keyboard shortcuts
These are useful shortcuts that can be added to the existing ones.

- Meta - ENTER 	: Terminal programme (e.g. Konsole)
- Meta - SPACE 	: Runner - to start programmes (remap the existing entry)
- Meta - S 		: LXQt settings (lxqt-config)
- Meta - B to 	: Brightness settings. Close with ESC after brightness change (lxqt-config-brightnes)

`LXQt settings` -> `Shortcut Key` -> `Add..`

To add a new shortcut press the empty field next to `Shortcut`. You can then choose the key combination you want like `Meta + S`. Add a description, tick `Command` for Type and then add the programme name to execute.

#### Openbox window manager keyboard shortcuts

Settings for window management like: make the window fill the left half of the screen are setup with Openbox. However, there is no GUI dialogue.

Instead the file `~/.config/openbox/lxqt-rc.xml` needs to be edited. As the name says the format is XML which makes the file very structured and okish readable.

You can set up a lot of things but here are my favourites:

1. Move a window to the full left/right half of the screen. This way you can comfortably have two programmes next to each other on one desktop.

2. Center a window in the middle. This is a purely aesthetic function if you only have one window on a desktop for example, you can then see the desktop background left and right of the window. This works well if you work with more than one desktop (see below). 

3. Make the window occupy about 3/4 of the desktop. That way you get a lot of space   for e.g. editors  and you leave room for something smaller. Or combine it with item 2 and centre the window.
special list.

4. Switch between desktops. This can actually also be done with the LXQt setting. 

5. Move a window to another desktop.
The last two shortcuts are really useful if you decide to use more than one (virtual) desktop as described next.

See the [Openbox docu](http://openbox.org/wiki/Help:Contents) for details.

So here are examples how to set the 5 functions above up.

All keyboard related settings in `~/.config/openbox/lxqt-rc.xml` are between <keyboard> and </keyboard>. So only make changes here.

Every shortcut definition is framed by `<keybind>` and `</keybind>`. Within the keybind an action is defined. The details to actions an parameters are described in the [Openbox docu](http://openbox.org/wiki/Help:Contents).

##### 1 Move a window to the full left half of the screen

```
<keybind key="W-Left">
      <action name="UnmaximizeFull"/>
      <action name="MaximizeVert"/>
      <action name="MoveResizeTo">
        <width>50%</width>
      </action>
      <action name="MoveToEdge">
        <direction>west</direction>
      </action>
    </keybind>
```

Here are several actions that resize the window to half the scree size and then move it over to the left screen edge. 

The shortcut assigned is Meta-Arrow Left. The "W" stands for windows key.

On the PinbookPro the Meta/Windows key and Arrow key combination currently does not work. No key signal is send if you press that combination, so unfortunately a substitute is required. e.g. "C-A-Left". That's Ctrl + Alt + Left arrow key. On the OG Pinebook the Window key works as expected.

##### 2 Center a window in the middle.

```
<keybind key="W-c">
   <action name="MoveResizeTo">
     <x>center</x>
     <y>center</y>
   </action>
</keybind>
```

Does what it says on the tin, it moves the active window to the centre of the desktop.

Assigned to `Meta + c`

##### 3 Make the window occupy about 3/4 of the desktop.

```
<keybind key="W-f">
   <action name="MoveResizeTo">
     <!-- adjust a window's height and width -->
     <width client="yes">3/4</width>
     <height>1/1</height>
   </action>
</keybind>
```    

This resizes the window so that it maximises to the top and bottom of the screen and uses 3/4 of the width left to right.

Assigned to `Meta + f`


##### 4 Switch between desktops

```
<keybind key="W-F2">
  <action name="GoToDesktop">
    <to>2</to>
  </action>
</keybind>
```

Activates Desktop 2

Assigned to `Meta + F2`. 

##### 5 Move a window to another desktop

```
<keybind key="W-S-F4">
  <action name="SendToDesktop">
    <to>4</to>
  </action>
</keybind>
```

Assigned to `Meta + Shift + F4`

After you have updated `lxqt-rc.xml` the command `openbox --reconfigure` will activate the changes or logout and login.

### More Desktops

The display of the Pinebook(Pro) is great, but like with any laptop it has only so much space and after a while a lot of windows overlap each other.

It can be quite practical to use more than one virtual desktop. This means that one program runs on one desktop and another on a different one and you can easily flip between them.

This avoids that many windows overlap each other. If shortcuts are set up to switch between desktops that can be a swift experience, however the mouse is also supported.

To set up 4 desktops: 

`LXQt settings` -> `Openbox Settings` -> `Desktop` -> `Number of Desktops`: 4

It might be helpful to organise apps by desktop. For myself I use this pattern (mostly)

- Desptop 1: For the terminal and settings and system tasks 
- Desptop 2: For the browser almost exclusively
- Desptop 3: Editors or generally for writing
- Desptop 4: Other stuff as it comes

To show the 4 desktops nicely in the panel right click the panel: 
- `Manage widgets` -> `Desktop switcher` -> `Number of rows`: 4

### Notifications

A small  thing is to set the time System notifications are shown. Default is 10 sec.

- `LXQt settings` -> `Desktop notifications` -> `Advanced settings` -> `Default duration`: 3 sec

### Session Settings

- add Firefox and your preferred  terminal to `Default Applications`
- `Basic Settings` ->  `Leave session` -> `Ask for confirmation..`: un-tick   (if you don't want to confirm that when you logout or shut down)

### Change CAPSLOCK to Menu

If you like me have no real use for the CapsLock key then one nice usage is to map the MENU key function to it.
This will basically make the CapsLock key behave as if you have pressed the right mouse button to get the context menu.

e.g. this is quite helpful for the auto-correct function in the browser, if you write for example in a forum you can get the auto-correct suggestions buy moving the cursor to a misspelled word and pressing CapsLock for the context menu instead of doing that with the mouse.

```
setxkbmap -option caps:menu
```

Add this line to your `.bash_profile` (There might be a better place for this but it works)

### Save git passwords with Kwallet

If you use git and want to save the git password in Kwallet then you can install `ksshaskpass` and add this line to the `.bash_profile`:

```
export GIT_ASKPASS='/usr/bin/ksshaskpass'
```

For more details and a solution for SSH keys. Check [here in the Archlinux Wiki](https://wiki.archlinux.org/index.php/KDE_Wallet#Using_the_KDE_Wallet_to_store_ssh_key_passphrases)

### Nextcloud auto login

If you are using nextcloud-client to sync your Nextcloud storage you will find that the nextcloud-client does not access the Kwallet correctly. 
This means in KDE your Nextcloud password will be safely saved in Kwallet, however that does not work with LXQt as of yet, a updated version is supposed to come.
In the meantime you can install `gnome-keyring`. That works.

## Home decorations

From here things are really personal taste, I will describe the changes I do to my setup and everyone can cherry pick what they like or use the info to adapt it to their taste.

### Panel on left side of screen

1. the most important thing for me is to move the Panel to the left of the screen (because I am used to that, not because it's better). 
They idea is that a laptop screen is quite wide but in comparison not very high, so this kind of maximises the height available for apps.
- right click on the panel
- `configure panel` -> `position`: Left of Desktop

2. If you move the Panel to the left (or right) of the screen, you have to do a few optical adjustments to make it work nicely.

- right click on the panel
- `Panel` -> `configure panel` -> `Size`: 65   (to make the panel a bit wider)
- `Panel` -> `configure panel` -> `Icon Size`: 32  (to adjust for the wider Panel)
- `Widgets` -> `Task manager` -> `Settings` -> `Button Style`: Icons only  (there is no space for the text)
- `Widgets` -> `Task manager` -> `Settings` -> `Maximum Button Height`: 65   (to allow for more icons in the Task manager)
- `Widgets` -> `World clock` -> `Settings` -> `General` -> `Autorotate ..`: Uncheck 

### Wallpaper and font

1. Set a wallpaper
- right click anywhere on the Desktop
- `Desktop Preferences` -> `Wallpaper image file`: choose wallpaper

For new open source wallpapers you can search at e.g. [Pexels](https://www.pexels.com/). 
For the Pinebook(Pro) use the size 1920 x 1080.

2. For the OG Pinebook you might want to change font sizes

For the PinebookPro the default settings are actually ok for me, but that also depends on preferences. 
I describe here how to adjust the font sizes with one example for the OG Pinebook and everyone can choose the best size for them.

- open LXQt Settings. 
- `Appearance` -> `Font` -> `Point Size`: 12
- `Appearance` -> `Font` -> `Resolution (DPI)`: 120
- `Openbox Settings` -> `Font`: +1 of current size

- right click Panel
- `Manage Widgets` -> `Application Menu` -> `Settings` -> `Custom Font size`: 14

### Icon set
The default Papyrus Icon set works okish for LXQt but you might want to be able to choose some other options. 

Here KDE comes in handy, in the KDE Settings for Icons you get an `Get new Icons` dialogue with a long list of options that you can install and you can also preview the icon sets. 
If you install an icon set with KDE you can then also use it with LXQt. 

As an alternative for many icon sets an AUR package exists. e.g. McMojave circle icons: `mcmojave-circle-icon-theme-git`. I would think that updates are smoother with AUR packages, but am not sure.

That said, my current favourite icon set is indeed McMojave Circle. It fits rather well with the default Manjaro Match Theme.

Please note that you can also set an icon set for the `Application Menu` separately in it's settings.

And last but not lest if you are not quite happy with the battery icon you can change that in the `LXQT Settings` -> `Power management Settings` -> `use icon from theme`. Maybe that icon is better.

### Kvantum Appearance tool

Kvantum (`kvantum-qt5`) is the Swiss army knife of desktop decoration for LXQt. 
It comes with a list of pre-installed themes and it's own configuration dialog in LXQt settings.

To use a Kvantum theme choose on in:
1. `LXQt settings` -> `Kvantum Manager` -> `Change/Delete Theme` -> `Select a theme`

If you want to use Kvantum you need to make some additional changes to the LXQt settings to make the most of it:

2. `LXQt settings` -> `Appearance` -> `LXQt Theme`: System
3. `LXQt settings` -> `Openbox` -> `Theme`: One of the `Kv..` themes that fits best.

- Setting a theme in the Kvantum settings dialogue changes mostly the look and feel of window content, like buttons and so on, 
- To set the Openbox settings to Kvantum changes the window decorations, like the title bar
- To set LXQT theme to System enables Kvantum to change the Panel and LXQt related appearance

More info to Kvantum and how to create your own themes [here](https://github.com/tsujan/Kvantum/tree/master/Kvantum) in the `doc` folder and the README.

### Activate items/icons per single click.

One setting that is certainly personal preference is single or double click activation. Originally many GUIs require a double click on a icon to initiate an action. More recently it is also possible to activate icons with a single click.

In LXQt there are several settings to activate single click consistently.

- `LXQt Settings` -> `Appearance` -> `Widget Style` -> `Activate item on single click`: tic

- `LXQt Settings` -> `Mouse and Keyboard` -> `Mouse` -> `Activate item on single click`: tic

- `PCManFM FileManager` -> `Edit` -> `Preferences` -> `Behaviour` -> `Open files on single click`: tic
