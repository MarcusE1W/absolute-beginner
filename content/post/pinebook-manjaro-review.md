+++
title = "Manjaro ARM on Pinebook"
date = "2019-02-02"
hide_authorbox = false
disable_comments = false
categories = ["Pinebook"]
tags = ["Manjaro"]
aliases = [""]
draft = true
+++

Feb 2019 review of Manjaro on Pinebook

<!--more-->



# Let's start

## Installation

## Works out of the box

## Errate

- Local settings dot no persist
- Sound widget in Panel seems not to work. After you select the mixer in the Panel  you can change the volumen there
- Display brightness cannot be changed with anything than the LXQt Widget.

  lxqt-config-brightness output:
     (0xffffe8317da8) Debug: No outputs have backlight property
     (0xffffe8317da8) Debug: Found output: "eDP-1"
     (0xffffe8317da8) Debug: Output: "eDP-1" added
     (0xffffe8317da8) Debug: Found output: "HDMI-1"
     (0xffffe8317da8) Debug: Output is not connected

- Icons in the Taskmanager are not centered whereas the icosn in the QuickLauncher are.
- Some LXQt widgets cannot be added to the Panel at all Sysinfo etc..
- Moving windows with the mouse can be very slow. The Graphic creates a tail effect.
  - Termite is super fast
  - File manager is so so
  - Emacs looks very strange
  - Firefox is super super slow
- sometimes the system just freezes, occasionally in small stepts -> rans out of memory ?
- suspend does not really wake up. it first shows the screen but then the display becomes dark and stays dark .. ?
-
