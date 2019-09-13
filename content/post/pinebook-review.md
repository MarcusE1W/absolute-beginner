+++
title = "Pinebook review"
date = "2019-01-19"
hide_authorbox = false
disable_comments = false
categories = ["Pinebook"]
tags = ["LXQt"]
draft = true
+++



# Pinebook: First impressions

Light, sturdy, plasticy but not in a bad way.

# The hardware
The display of the Pinebook is porbably the germ of this notebook. It is super sharp with a resolution of 1920x1080 and very much in difference to most cheap notebooks it is not glossy.
The display does hardly have any reflection at all.

The keyboard is actually quite nice to type on (I am doing it right now). It has a few quirks though.
- For uncomprehendable reasons the keys `'` and `"` are not directly mapped on the keyboard but require to press the `Fn` key. So to get the not unusual `"` you have to press Fn + Shift + -. Usable but a bit querky.

Another thing of notice is that the additional Super key between alt and Fn is mapped to MENU. Means it acts as if the second mouse key has been pressed. This is actually surprisingly useful, e.g. the spellchecking ooptions in many programms and the browser can be easily selected from the keyboard like this. However many window manager make also good use of a Super key for shortcuts like the Windows key on Windows notebooks or the Alt key on Macs. If you find yourself to prefer a Super key over a MENU key then luckily this can be easily remapped. XXX Link to something XXX

The last thing to mention is the trackpad. It is ok. Not more. The size is small, but that is not really a problem, however it does not feel very precise. Everything works, that's about it.

Battery life is for me in the area of 8 hours. Very usable anyway.

CPU speed and graphic speed seem ok. It's not super quick but feels responsive in alsmost all use cases.

In total with the great display and the light package this is a very nice little notebook that is very usable for many tasks. A great little notebook.

# The software
After the first startup of the Pinebook you are greeted with a KDE neon login screen. `user` `password` gets you to the KNE plasma desktop.
- many options of alternative Linux flavours



## Appearance
- LXQt theme: Ambiance
- Font: Point Size: 12
- Resolution (DPI) 120

# Panel
Size: 50
Icon Size: 32
Position: Left of Desktop

## Widgets

- Add spacer between quick launcher and task whatsnot
## Locate
- Set your location
- Does not work propperly yet

## Openbox Settings
- Font: All one up: 11 11 10 10 10 10 

# Wifi
Set `rtw_power_mgnt=0` in /etc/modprobe.d/8723cs.conf

# Keyboard
- To get the key between LShift and Z working correctly set the keyboard variant to `English (intl, with AltGr dead keys)`
- I think the SUPER/META key is very useful but I also learned to like the MENU key that is mapped in the pinebook between FN and Alt. So I suggest the following mapping: MENU -> META, CapsLock -> MENU.

```
setxkbmap -option caps:menu,altwin:alt_super_win
```


I have added this to .bash_profile but I am sure there is a better more Xorg like way. Still, it works.

# Touchpad acceleration and scroll direction.

To set touchpad parametres from the cli you can use the command xinput.
To use it correctly you first need to determine the device id / name for your touchpad. Use 
```
xinput list` 
```
to do so.

You are looking for a line like this:
```
HAILUCK CO.,LTD USB KEYBOARD Mouse      	id=7	[slave  pointer  (2)]
```

With the device id = 7 found you can list the parameters that can be set with xinput.

```
xinput list-props 7
```

The result looks similar to this:
```
device 'HAILUCK CO.,LTD USB KEYBOARD Mouse':
...
libinput Natural Scrolling Enabled (256):	0
...
libinput Accel Speed (265):	0.000000
...
```

To change the parameter use `xinput set-prop`

To set reverse scrolling for the touchpad use this command 
```
xinput set-prop 7 "libinput Natural Scrolling Enabled" 1
```

To set mouse speed
```
xinput --set-prop 7 'libinput Accel Speed' 0.95
```

For more details on xinput and mouse speed also see the [Archlinux Wiki]( https://wiki.archlinux.org/index.php/Mouse_acceleration#Using_xinput)


# Bluetooth
To get bluetooth working I installed these packages and used `bluetoothctl` to set it up for an external keyboard and loudspeaker. Works but the setup took a moment. 
- bluez-utils
- pulseaudio-bluetooth
- blueman

This [guide in the Archlinux Wiki](https://wiki.archlinux.org/index.php/Bluetooth#Pairing) was helpful.

## bluetoothctl

- power on
- scan on
- devices
- info B8 - Sony
- info C.. Lofree
- connect

## blueman
GTK3 frontend to set up and manage bluetooth

# Font size and adoption to high(er) resolution display
- LXQt Setting Appearanc: set Font Point size to 12
- LXQt Setting Appearanc: Resolution (DPI) to 120
- LXQt Setting Openbox: Font: Add 1 to all font sizes to 11 11 10 10 10 10
- Firefox: In about:config set layout.css.devPixelsPerPx = 1.4
- Firexox: In Preferences:Font:Advanced set Minimum fot size to 16

# LXQt shortcuts to support window management

All these changes require that the META key is available and mapped as described in 2) The following mappings are inspired by some windows functionality and also a lot from tiling WMs. This setup was so useful that for the moment I stopped using a tiling wm. 
 
So to start I have activated 4 desktops in the openbox settings.

In LXQt Settings -> Shortcuts I have added these keybindings:

| desciption                     | key          |
| ---                            | ---          |
| Move to desktop 1              | META + 1     |
| Move to desktop 2              | META + 2     |
| Move to desktop 3              | META + 3     |
| Move to desktop 4              | META + 4     |
| Open Terminal                  | META + Enter |
| Open Runner to start programme | META + Space |


# Openbox shortcuts for window management

This part of the openbox configuration should be added to file: `.config/openbox/lxqt-rc.xml` behind all other `<keybind>` and before `</keyboard>`

The following keybindings get implemented:
| desciption                                                 | key                         |
| ---                                                        | ---                         |
| Move  window to desktop 1                           | META + Shift + 1            |
| Move  window to desktop 2                           | META + Shift + 2            |
| Move  window to desktop 3                           | META + Shift + 3            |
| Move  window to desktop 4                           | META + Shift + 4            |
| Maximise  window                                    | META + Arrow Up             |
| Unmaximise  window                                  | META + Arrow Down           |
| Move and resize  window to left half of the screen  | META + Arrow Left           |
| Move and resize  window to right half of the screen | META + Arrow Right          |
| Maximise only vertically (max upper and lower display edge | META + Fn + Arrow Up (PgUp) |
| Maximise vertically and increase size horizontally         | META + f                    |
| Center  window                                      | META + c                    |

This is the config:
```
    <keybind key="W-S-1">
      <action name="SendToDesktop">
        <to>1</to>
      </action>
    </keybind>
    <!-- Keybinding to move window to desktop 2 -->
    <keybind key="W-S-2">
      <action name="SendToDesktop">
        <to>2</to>
      </action>
    </keybind>
    <!-- Keybinding to move window to desktop 3 -->
    <keybind key="W-S-3">
      <action name="SendToDesktop">
        <to>3</to>
      </action>
    </keybind>
    <!-- Keybinding to move window to desktop 4 -->
    <keybind key="W-S-4">
      <action name="SendToDesktop">
        <to>4</to>
      </action>
    </keybind>
    <!-- Keybinding to maximise window-->
    <keybind key="W-Up">
      <action name="Maximize"/>
    </keybind>
    <!-- Keybinding to unmaximise window -->
    <keybind key="W-Down">
      <action name="Unmaximize"/>
    </keybind>
    <!-- Keybinding to move window to the left or right half of the desktop -->
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
    <keybind key="W-Right">
      <action name="UnmaximizeFull"/>
      <action name="MaximizeVert"/>
      <action name="MoveResizeTo">
        <width>49%</width>
      </action>
      <action name="MoveToEdge">
        <direction>east</direction>
      </action>
    </keybind>
    <!-- Keybinding to maximise the window to the top and bottom but leave the width as is-->
    <keybind key="W-Prior">
      <action name="MoveResizeTo">
        <!-- adjust a window's height and width -->
        <!-- <width client="yes">2/3</width> -->
        <height>1/1</height>
      </action>
    </keybind>
    <!-- Keybinding to maximise the window to the top and bottom -->
    <keybind key="W-f">
      <action name="MoveResizeTo">
        <!-- adjust a window's height and width -->
        <width client="yes">3/4</width>
        <height>1/1</height>
      </action>
    </keybind>
    <!-- center the window on the first monitor -->
    <keybind key="W-c">
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
      </action>
    </keybind>
```

 
# Shortcuts

Principle approach
Meta: 	for DE
Ctrl: 	for Apps
Alt: 	for User and Extensions

Allow for common exceptions like Alt+TAB

META 1/2/3/4 to activate desktop/workspace
Shift META move window to another desktop and switch to that desktop
META-Space - Start programme with Runner, the LXQt app starter
META-Enter - Start new Terminal


# Additional Packages
trizen
git
htop
emacs (spacemacs)
fakeroot


# Niggels
- Setup in Manjaro-settings seems not to work
	- Timezone
- Window movement is suspiciously slow and runs over..
	- transparency in the kvantum manager seems to help a bit
	- in openbox settings untick change window while moving (does that do anything ?)
- Window size is not saved
- Sound does not work out of the box for newly set up user. the original manjaro user should work
- bluetooth not installed correctly ?
- LXQt settings: mouse acceleration seems not to work -> xinput
- power management
    - wifi power management has to be turned off
    - how does sleep actually work
    - the display seems not to turn off completely ?
- LXQt settings: reverse scrolling does not work -> xinput


# Kernel stuff

```
using r6p2.
Since that has both fbdev and x11 drivers.
Pine64Bot
<jernej> ok, good
P
<jernej> then download https://developer.arm.com/-/media/Files/downloads/mali-drivers/kernel/mali-utgard-gpu/DX910-SW-99002-r9p0-01rel0.tgz
<jernej> and apply patches located here: https://github.com/LibreELEC/LibreELEC.tv/tree/allwinner/packages/linux-drivers/gpu-sunxi/patches
Strit
Aren't it the same as: https://github.com/mripard/sunxi-mali ?
Pine64Bot
<jernej> no
P
<jernej> some is simplified and some omitted
<jernej> I mean patches
<jernej> driver source is newer
<jernej> I build it with:
<jernej> make -C $(kernel_path) M=$PKG_DRIVER_DIR MALI_PLATFORM_FILES=platform/sunxi/sunxi.c \
<jernej> EXTRA_CFLAGS="-DCONFIG_MALI_DVFS -DMALI_FAKE_PLATFORM_DEVICE=1 -DCONFIG_MALI_DMA_BUF_MAP_ON_ATTACH" \
<jernej> CONFIG_MALI400=m CONFIG_MALI_DVFS=y CONFIG_MALI400_DEBUG=y
<jernej> where $(kernel_path) is path to kernel headers
<jernej> and $PKG_DRIVER_DIR is the path to kernel driver top directory, something like "driver/src/devicedrv/mali/"
```
