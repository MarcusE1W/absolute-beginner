
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

## Introduction
Oni is an editor that is based on neovim and uses electron and node.js to create a modern graphical user interface. This allows a modern look and still a decent platform independent development. For those familiar with the electron editors like Atom and VScode one interesting question might be how fast `oni` feels in comparison. The good new is that oni starts really quite quick even in my VirtualBox Linux and feels quite responsive.

## Edit
dies und das und jenes

3. Ctrl-v klappt shon mal in insert mode. wie kann man denn text selektieren ?
4. Ctrl-s klappt nicht in insert mode.

## Navigation
- What is the difference between tab/buffer/window ?
- Move between splits: Ctrl-w <arrow>
## Tabs
How to switch tabs with the keyboard?
Update: Accuidentially pressen Ctrl-Shift - Up/Down (insert/normal) and that does it.
Update: Now Ctrl-Shift - PageUp/PageDown works as well. I thought I tried this before ?
### Themes
Doku says themes to be set in config. Which themes are available ? Maybe the docu can mention the command palette?
## User
User

### command palette /  <command> menu

??? What do I want to say here???
- Command palette shortcut only works in normal mode? Is that correct ? Is it correct that in insert mode Ctrl-Shift-P is a for of autocompletion ?
I think the command palette should support (next to others) these functions:
- discoverability: It should be easy and to find functions that you assume are there but have not learned about yet. Also it shold be possible just to browse and be able to find new functions. This is working for the comand palette, but not for the vim : commands?
- learn shortcuts: you don't know all shortcusts yet, but you can use the function from the command palette and the shortcut is also listed there. Next time you remember.

- It is unclear for me how these two menues play together.
- All commands relevant for navigation (tabs/buffers/etc.) should be in here. (open, split, close, move, etc)

### Explorer
- How to navigate? j,k,h,l usw
A starting point is to use Ctrl-g. But not sure yet if thats enough? How do I select something that a file that is currently not shown in the Explorer

| function                 | keys           |
| ------------------------ | -------------- |
|

- how can it be activated ?
Sort sequence a bit strange. First a few .folder then All normal folder in a sorted way and then more .folder
folder
### Search / Query
- Not really sure what that thing does. Some new window gets opened. How to close that again? Ah, :q . This is propabbly a neovim function despite the GUI interface.:
- Open sidebar file finder: Ctrl-Shift-e 
    - then key in your search
    - press <esc> 
    - <arrow keys> to navigate up down to the right file

## Configuration

The command: `Configuration: Edit user config` opens a file `config.tsx` in what looks like a split screen. The right side resembles the configuration file in the docu. What is the left side document? Why are there seemingly two seperate docs under one name (tab)?

Update: So, Is the one file the standard configuration and the other one is the user configuration ?

Update: I guess the configuratin workflow is to check in the standard file (left) and copy that over to the user config (right). It would be good to explain how to do this for a novice with the keyboard/shortcuts. Like go to standard window/buffer ?. this is how to select something, this is how to move to the right window. Might be worth a tutorial task if that's possible

I think it would be great if it were possible to have autocompletion for possible configuration values (e.g. all the availabe themes)

### Shortcut configuration
- How to distinguish between modal and insert mode? Are shortcusts always available ? It does not look like that.
- How do I find the right functioin to bind the shortcut to? I have for example found `:tabNext` to move to the next tab. How do I bind this to e.g. Ctrl-PageDown ?
- Ctrl- shortcuts in modal or insert mode?

## Markdown support
- Headlines, lists and links work well.
- The preview is in sync with what is shown in the editor. A great plus over many other markdown preview plugins.

**dies**
_jenes_
[hier](heise.de) auch nich so pralle

| dies | das |
| ---  | --- |
| tescht | tescht |

- use commands in the command palette to turn preview on and off
- no table support in the moment

## Edit


| key | description                                                    |     |
| --- | -------------------------------------------------------------- | --- |
| Ctrl-V | paste. **(seems to be limited to 628 lines)**|
| Ctrl-C | copy ? wie geht das? |
| Ctrl-X | ist das ueberhaupt definiert ? |

### Comment and uncomment text

| key | description                                                    |     |
| --- | -------------------------------------------------------------- | --- |
| ggc | comment/uncomment the current line                             |     |
| gc  | comment/uncomment the current selecton (marked in visula mode) |     |


###  basic vim keystrokes
| function                                           | normal mode |
| ---                                                | ---         |
| copy (yank )marked selection or char under cursor  | y           |
| paste (insert)                                     | p           |
| cut character under cursor                         | x           |
| enter visual mode for selections                   | v           |
| enter visual mode for whole line selections        | V           |
| enter insert mode to write text.                   | i           |
| leave insert mode to execute commands.             | ESC         |
| move (or select) to the beginning of the next word | w           |
| move (or select) to the end of the current word    | e           |
| save                                               | :w          |
| close buffer                                       | :q          |
| save and close buffer                              | :wq         |
| delete until next . (sentence end) | df. |
| one word right      | w           | Ctrl-arrow-left |
| one word left       | b           | Ctrl-arrow-left |




| function                              | keys  |
| ---                                   | ---   |
| add a new line over the current line  | [ SPC |
| add a new line under the current line | ] SPC |

| function                 | keys           |
| ------------------------ | -------------- |
| multiple cursor row down | Shift-Alt-Down |
| multiple cursor row up   | Shift-Alt-Up   |


### General
| function                 | keys           |
| ------------------------ | -------------- |
|
### File mgt.
open
| function                 | keys           |
| ------------------------ | -------------- |
|
### Tabs
| function                 | keys           |
| ------------------------ | -------------- |
| one tab right | Ctrl-Shift-PageDown
| one tab left | Ctrl-Shift-PageUp


### Themes
- Why can an oni-theme in the baseVimTheme qualifier of an original  oni-theme be successfully read, and if so why does it overwrite what comes after it in the original oni-theme?
- Although it says vim-themes are optional they arent. If you don't put one yourself neovim will decide for one.
- why does the editor qualifier change the Explorer ?
- if some text is folded like in gruvbox then 'l' opens it up
- if the theme does not load because something is not right, change to another (standard) theme, there is a error highlighting for json format errors.
### markdown
- markdown preview pops up every time the oni screen get's shown and activated (spectrwm)

### Search & Replace
- search works with `/`
- dann gibt es `Ctrl-/`
- wie geht replace ?


## Things not working as expected:
- Ctrl-o: to open a file (menu works)
- Ctrl-n: to open a new empty buffer?
- Ctrl-s: save file in insert mode.
- Ctrl-tab: shows the open buffer list: command palette command does nothing
- C-S-P: command-palette: show buffer list does nothing
- Activation of explorer

## Vertical selection
Visual-block Insert						*v_b_I*
With a blockwise selection, I{string}<ESC> will insert {string} at the start
of block on every line of the block, provided that the line extends into the
block.  Thus lines that are short will remain unmodified.  TABs are split to
retain visual columns.
See |v_b_I_example|.


Visual-block Append						*v_b_A*
With a blockwise selection, A{string}<ESC> will append {string} to the end of
block on every line of the block.  There is some differing behavior where the
block RHS is not straight, due to different line lengths:

1. Block was created with <C-v>$
    In this case the string is appended to the end of each line.
2. Block was created with <C-v>{move-around}
    In this case the string is appended to the end of the block on each line,
    and whitespace is inserted to pad to the end-of-block column.
See |v_b_A_example|.
Note: "I" and "A" behave differently for lines that don't extend into the
selected block.  This was done intentionally, so that you can do it the way
you want.


Visual-block change						*v_b_c*
All selected text in the block will be replaced by the same text string.  When
using "c" the selected text is deleted and Insert mode started.  You can then
enter text (without a line break).  When you hit <Esc>, the same string is
inserted in all previously selected lines.


Visual-block Change						*v_b_C*
Like using "c", but the selection is extended until the end of the line for
all lines.


								*v_b_<*

Visual-block Shift						*v_b_>*
The block is shifted by 'shiftwidth'.  The RHS of the block is irrelevant.  The
LHS of the block determines the point from which to apply a right shift, and
padding includes TABs optimally according to 'ts' and 'et'.  The LHS of the
block determines the point upto which to shift left.
