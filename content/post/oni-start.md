
+++
title = "Oni Editor for beginer"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Oni", "Vim"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

An introduction into the new oni editor

<!--more-->
# First impression of the oni editor

## Installation
The installation in Archlinux is really easy. Oni is an AUR package in the moment.  I use the AUR helper `trizen` so my command is:
```bash
trizen -S oni
```

More instructions can be found in the [oni wiki](https://github.com/onivim/oni/wiki/Installation-Guide)

## First Impressions
Oni is an editor that is based on neovim and uses electron and node.js to create a modern graphical user interface. This allows a more modern look and still a decent platform independent development. For those familiar with othe relectron editos like Atom and VScode one interesting question might be how fast `oni` feels in comparison. The good new is that oni starts really quite quick even in my VirtualBox Linux and feels really responsive.

## tescht
dies und das und jenes 

- turn out I am on the old 0.3.1 version. no tutorial, no markdown-preview or so..
- die font unschaerfe is etwas seltsam.

1. Ich will all diese vim hilfen die man so sieht..
2. warum da nur ein par befehle in der commman pallette sind, is mit nicht klar.
klar.
3. Ctrl-v klappt shon mal in insert mode. wie kann man denn text selektieren ?
4. Ctrl-s klappt nicht in insert mode.

### Tabs
How to switch tabs with the keyboard
Update: Accuidentially pressen Ctrl-Shift - Up/Down (insert/normal) and that does it.
### Themes
Doku says themes to be set with XXX. Which themes are availablew ?
Update: Found the command palette function function

## User interface


### command palette /  <command> menu

??? What do I want to say here???
- Command palette shortcut only works in normal mode? Is that correct ?
I think the command palette should support (next to others) these functions:
- discoverability: It should be easy and to find functions that you assume are there but have not learned about yet. Also it shold be possible just to browse and be able to find new functions. This is working for the comand palette, but not for the vim : commands?
- learn shortcuts: you don't know all shortcusts yet, but you can use the function from the command palette and the shortcut is also listed there. Next time you remember.

It is unclear for me how these two menues play together.

###   
- Ctrl- shortcuts in modal or insert mode?

### Explorer
How to navigate?

## Configuration

The command: `Configuration: Edit user config` opens a file `config.tsx` in what looks like a split screen. The right side resembles the configuration file in the docu. What is the left side document? Why are there seemingly two seperate docs under one name (tab)?

I think it would be great if it were possible to have autocompletion for possible configuration 
### Shortcut configuration
- How to distinguish between modal and insert mode? Are shortcusts always available ? It does not look like that.
- How do I find the right functioin to bind the shortcut to? I have for example found `:tabNext` . How do I bind this to e.g. Ctrl-PageDown ?
