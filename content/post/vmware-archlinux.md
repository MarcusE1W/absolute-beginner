+++
title = "Set up VM Ware for Archlinux"
date = "2018-12-07"
categories = ["Linux"]
tags = ["VM"]
draft = false
+++

VM Ware archlinux setup
<!--more-->


# Install

- git
- yay
- xorg-server
- micro-nightly-bin
- xclip
- xorg-xinit
- xterm

# spectrwm
	- cp /etc/spectrwm.conf ~/.spectrwm.conf
	- edit spectrwm.conf: bar_font		= xos4 Terminus:pixelsize=14:antialias=true
	- set 'program[term] = termite'

# xorg-xrandr
	- check monitor and resolution mode with: 'xrandr'
	- add to .xinitrc: 'xrandr --output Virtual1 --mode 1360x768'
	
# firefox

# termite
	- mkdir .config/termite
	- cp /etc/xdg/termite/config ~/.config/termite/config
	- edit font size
	- change termite colour scheme fot more contrast

# exa
	- change fish func for ll to exa -l

# kitty
