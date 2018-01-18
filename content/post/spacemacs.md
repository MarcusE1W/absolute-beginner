+++
title = "Spacemacs for beginner"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Spacemacs"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

An introduction into the Spacemacs editor for a user with little editing experience.

<!--more-->

# Spacemacs for Beginner

Spacemacs is a beginner friendly extension of the very capable editor Emacs. One potential down-side for the beginner is that there is a lot of functionality available and you have to find out what is the most useful first. To help with this Spacemacs has a clever menu system that shows you the available functions and the neccessary key strokes.

## Areas you need to know about
- What are the different selection screens like
  - The Spacemacs SPC menu (Which-key)
  - The helm or ivy menu to select in listsP
- How to do basic configuration changes
- How to use the text editing and many more commands that Spacemacs offers
- And last but not least, how to discover new (as in unknown to you)functions in Spacemacs by yourself.
- Adjust the theme and font used

### Executing commands in Spacemacs
The main way to execute commands is to press SPC (the space key) and then a kombination of keys for the specific command. Once `SPC` has been pressed a menu opens that shows the possible keys. E.g. SPC f s saves the current buffer. It is probably worth just to try a few commands that look interesting to you. For your experiments maybe have a file available that you can load just for testing.

### Opening files
There are several ways to open a file, but a good start is the file selector Neotree, activated with `SPC f t`.
Move to the neotree window with SPC 0 and back to the other previous buffer with it's number (SPC #).
Show content of a sub-folder with RET or l (list?).
Rename a file with r. Create a new file with c (create).
Press s to toggle between hidind and showing hidden files.

### Basic Spacemacs Evil (Vim) commands
There are (I am sure but have not made it that far yet) usefule vim commands to edit your text and work with the editor. I think as a beginner you don't need all of them. So here are some vim commands that are useful to have a good start and which are, I think also quite easy to remember.
The vim mode is a so called modal model. This means it has several different modes that are specialised in doing one thing especially good. The Spacemacs documentation describes this very well. Spacemacs also shows a different colour for the window number depending on your mode.

- Normal mode (ESC). This is where you execute vim commands and edit text, not to write text. To write text you switch to insert mode.
- Insert mode (i). Use insert mode to write text. some more basic text editing also works here.
- Visual mode (v/V) This is where you select text. Change to visual mode and select text. Then execute commands. You can execute vim commands like copy but you can also execute the SPC sommands from spacemacs that are relevant for text selection.

| function                                           | normal mode | alternative |
| ---                                                | ---         |             |
| copy (yank )marked selection or char under cursor  | y           |             |
| paste (insert)                                     | p           |             |
| cut character under cursor                         | x           |             |
| enter visual mode for selections                   | v           |             |
| enter visual mode for whole line selections        | V           |             |
| enter insert mode to write text.                   | i           |             |
| leave insert mode to execute commands.             | ESC         |             |
| mark (unmark) a selection as comment               | gc          | SPC c l     |
| move (or select) to the beginning of the next word | w           |             |
| move (or select) to the end of the current word    | e           |             |
| save                                               | :w          | SPC f s     |
| close buffer                                       | :q          | SPC b d     |
| save and close buffer                              | :wq         |             |

<!-- Spacemacs 2 -->
<!-- example for mass processing of a text block: Ctrl-v, mark lines, i, write text, <ESC>  -->
<!-- Example for mass processing at end of line: Ctrl-V, mark lines, $A, write text, <ESC> -->


### Window handling
Windows are the text areas you see in Spacemacs. When you start it is usually one window. You can split the screen to see two or more windows at the same time.

Additinally spacemacs uses the term buffer. buffer are effectively your text file. You can have a large number of buffers open but only show a few in windows.

To keep an overview there are several SPC commads to manage windows and buffer.

### Close a window or buffer
- `SPC w d`. This will close the currently active window. The buffer is still open but not visible and you can continue writing at a later time.
- `SPC b d`. This will close the buffer (file). That means either you have saved the text or you will be asked to save it and then it is closed. the window however will stay open and a differnt buffer will be shown in this window. Confusingly it can happen that the same buffer (file) is shown in two windows. In that case you probaly don't need all the windows and you can close one with `SPC w d` or open another file in the second window.


### Show a different buffer (file) in your current window.
If you have several buffer (files) open and want to show a different buffer file in your current window then open the buffer selection screen (SPC b b) to jump to other open buffers (files)
- SPC <buffer-number>

### Search in buffer
- SPC s s -
- Alternatives: / SPC s project something

Spacemacs offers quite a lot of functionality to search either in open buffers or also in project folders. Worth exploring.

### Move in the current buffer

Vim (and Spacemacs uses a Vim emulation) is famous for beeing a modal editor. That means basically it has one mode to write text called `insert mode` and some other modes to work with and format the text. Hence the name modal. The most important of these functional modes is `normal mode`. When you start spacemacs it will be in normal mode first. You can see that parts of the mode line are yellow.

| function            | normal mode | alternative     |
| ---                 | ---         | ---             |
| one character left  | h           | arrow-left      |
| one row down        | j           | arrow-down      |
| one row up          | k           | arrow-up        |
| one character right | l           | arrow-right     |
| one word right      | w           | Ctrl-arrow-left |
| one word left       | b           | Ctrl-arrow-left |

The idea behind the hjkl keys for cursor movement is that the hands have not to move from the base key line of your keyboard to move the cursor. The base row is the middel row of characters on your keyboard. This way your hads do not have to move around so much to reach the arrow-keys or the mouse. However,  you can also use the arrow keys.

- In insert mode the arrow keys, page-up, page-down, Home and End keys can be used.

__Bonus function__
A very nifty function to jump quickly to text currently displayed in the window is `SPC j j`.
- After the second j of the SPC command select the first letter of the text where you want to jump to. So basically look at the word you want to jump to and select it's first letter.
- All the corresponding letters in the visible text of the window will be marked with a two letter combination.
- Key in the two colourful letters of the positionat the beginning of the word where you want to jump and there you are.
- It is much more straight foreward than it sounds.

Example text:
### Text manipulation

To be found in sub-menu SPC x...
Lots of interresting stuff there like:
- Move lines up and down. To move your current line up or down use `SPC x K` for up and `SPC x J` for down. This also works with selections.
- Uppper/lower case text selections (`SPC x U` for upper and `SPC x u` for lower case)
## Configuration
As mentioned in many places, confiuration  in Spacemacs happens in the .spacemacs file. The file is largely split in 5 interestin sections:

..... some comments at the top

`(defun dotspacemacs/layers ()` ... some standard configuration

`Dotspacemacs-configuration-layers` ... add layers after that some more standard configuration

`(defun dotspacemacs/user-init ()` ... setup for the very start of emacs, not often needed
`(defun dotspacemacs/user-config ()`... your personal user configuration
`(defun dotspacemacs/emacs-custom-settings ()` ... don't make changes after this
1. In the first section you find already predefined configuration functions with default settings
2.

NOTE: the whole large section of standard configuration is called `(defun dotspacemacs/layers ()` whereas the small paragraph where you add your own selection of layer is called `dotspacemacs-configuration-layers**.

## Text editing in Vim normal mode 

Here are some more useful commands for normal vim mode of Spacemacs

**Text selection**
| function                         | keys |
| ---                              | ---  |
| select the word under the cursor | viw  |
| cut the word under the cursor    | diw  |
| copy the word under the cursor   | yiw  |
| cut the current line             | dd   |

**Add more space**
Often you want to add more text in your existing document and for that you need space. Either empty lines or just some space characters. sometimes you just want to add this and sometimes it is usefull to enter insert mode to start writing. So here are some useful normal mode commands to add more space.

| function                              | keys  |
| ---                                   | ---   |
| add a new line over the current line  | [ SPC |
| add a new line under the current line | ] SPC |
|                                       |       |

## Useful links:

- An absolute beginners guide to Spacemacs for academic (writing)[https://ontologicalblog.com/2016/10/14/an-absolute-beginners-guide-to-spacemacs-for-academic-writing/]

## Explanation of Emacs specific jargon
| Emacs  | Description |
| ---    | ---         |
| Kill   |             |
| Buffer |             |
| Layer  |             |
|        |             |


### Functions

Function refers to the thing that you are calling when you hit a key or series of keys. For example j in normal modeis mapped to the function evil-next-line. In elisp these usually look like strings of hyphenated words. spc spc opens helm M-x and lets you search for functions by name and execute them. Note that functions may also be refered to as sexps (symbolic expressions).
### Buffers

Buffers are like tabs in your browser. You open them from files on your computer instead of from the internet, and they stay open until you close them. Hit spc b b to see a searchable list of your open buffers, and recently opened buffers. spc b B opens a list of buffers organized by major mode. spc b d deletes the buffer you are currently in. As you can most the spc b commands are related to buffers. But buffers arent necessarily just files you open, they can also be generated by emacs (like the helm mini buffer (spc b b) you use to search buffers) to do useful things.
### The Mode Line

At the bottom of the window, you will see the mode line. Its got some handy information in it. From left to right it shows you:

- Your window number. The color indicates what evil mode you are in (normal, insert, etc)
- A little * indicator if your file has been modified since it has been saved.
- Buffer size.
- Buffer name (same as file name if you have opened from file).
- Major mode.
- Minor modes.

On the far right is info about where you are in a buffer. Move around whth hjkl and watch it if you dont get it at first.
### Major Modes

This is how emacs organizes important sets of functionality. Each buffer will have one major mode at a time. It can customize anything about emacs so that it suits the buffer you are working with. There is a mode for editing C#, a mode for editing latex, a mode for viewing files (dired-mode), a mode for searching (helm-major-mode), a mode for emulating a terminal (term-mode). You can see what major mode you are in at the bottom of each buffer in your mode line. Usually this is automatically set depending on which buffer you are in. Major modes specific functions are on the , key (also spc m).
### Minor Modes

Minor modes are smaller sets of custom behavior that can work together. A major mode will automatically set a bunch of relevant minor modes, but you can toggle them with spc t. For example spc t n toggles a minor mode for line numbers. You can hover over the symbols in the modeline with your mouse to see what minor mode each represents. spc h d m (help describe mode) opens a comprehensive list of your active minor modes. Move your cursor to one and hit enter to get more information.

Side Note: The information opens in a split buffer titled *help*. Many of these buffers that are meant to be temporary can be closed quickly with q.

### Layers

Everything so far (except specific key bindings) applies to emacs in general. Layers, however, are a spacemacs specific term. Layers are meant to be a simple way for you to customize your configuration by adding only one line to your .spacemacs file. See the list to see what are available. Check out the latex layer for example.

### The .spacemacs file

Hit spc f e d (file emacs dotfile) to open this file. This is where you can customize everything. Find the dotspacemacs-configuration-layers line. You can use / in normal mode to start searching for it and enter when you have it. Add latex in that list. It should look like this:

dotspacemacs-configuration-layers '(
latex
other-layer
other-layer)

Now spacemacs will load that layer on startup for you, which includes a major mode for editing latex and a bunch of commands. You can now either restart emacs, or hit spc f e R(file emacs reload) to reload your config. Now if you hit spc f f (file find) and open a latex file you should have some syntax highlighting and latex specific commands on your , key.
