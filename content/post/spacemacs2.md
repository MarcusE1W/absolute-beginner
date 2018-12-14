+++
title = "More Spacemacs"
date = "2018-03-30"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Spacemacs"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

More Spacemacs tips and setup

<!--more-->



[Edit docu](https://spin.atomicobject.com/2017/08/31/awesome-spacemacs-features/)

# More Navigation

## Move lines up and down
To  make this tip work you have to change the _dotspacemacs-visual-line-move-text_ variable in the _.spacemacs_ file

```
;; If non-nil, `J` and `K` move lines up and down when in visual mode.
;; (default nil)
`dotspacemacs-visual-line-move-text t 
```

Once the change is done you van enter visual mode and move the current (selected) line up and down with J and K. 

# Spacemacs 2
example for mass processing of a text block: Ctrl-v, mark lines, i, write text, <ESC>
Example for mass processing at end of line: Ctrl-V, mark lines, $A, write text, <ESC>


Spacemacs 2
### Text manipulation

To be found in sub-menu SPC x...
Lots of interresting stuff there like:
- Move lines up and down. To move your current line up or down use `SPC x K` for up and `SPC x J` for down. This also works with selections.
- Uppper/lower case text selections (`SPC x U` for upper and `SPC x u` for lower case)

TODO: - Describe how to set variables.

## Improved Spacemace experience

### Treemacs
If you are on the develop branch (as of Dec 2018 but that might change) then you have the option to replace neotree with treemacs. Treemacs looks more pretty and has a consisten key mapping.

To install just add `treemacs` to the list of layouts.

### Modeline with all-the-icons
**Note:** It seems that this adds quite some time to Emacs startup time.

All the icons makes the modeline more pretty.

https://github.com/domtronn/spaceline-all-the-icons.el

While all-the-icons is quite pretty and works fine it seems to add quite some time to the start-up. So if you experience this you might either want to turn it off already or consider daemon mode.

### Daemon mode

If you start emacs in daemon mode emacs will start once with the normal startup time and then stay in the background even if the window gets closed. The next time emacs gets started it starts almost instantly.

I find this especially usefull in terminal mode. To start a window in terminal mode use `-nw`. The `-a ""` parameter starts a new daemon or uses an existing one. You can add a file name at the end to open that.

```
emacsclient -nw -a "" <file>
```
To close an emacs window without closing the emacs daemon use `SPC q f`

As the command above is a bit on the lengthy side it might be useful to create an alias and add that to you `.bashrc` or the setup for the shell you are using.

If you install the all-the-icons spacebar the terminal mode spacebar looks almost like tthe graphic one. And as you start the daemon only onece the startup time is not as important.

### Font

The standard XXX font works well, if you are looking for a slightly different font, I have good experiences with `Iosevka Term`.

To add it to spacemacs you first need to install [Iosevka](https://be5invis.github.io/Iosevka/).

You can check with `fc-list` in the terminal if the font has been installed sucessfully.

Then change this part of your .spacemacs config:

```
   ;; Default font, or prioritized list of fonts. `powerline-scale' allows to
   ;; quickly tweak the mode-line size to make separators look not too crappy.
   ;; dotspacemacs-default-font '("Source Code Pro"

   dotspacemacs-default-font '("Iosevka Term"
                               :size 15
                               :weight normal
                               :width normal)
```

Save with `SPC f s` and restart with `SPC q R`.

# Spacemacs (Emacs) terminology

## Explanation of Emacs specific jargon
| Emacs     | Description                       |
| ---       | ---                               |
| Kill      |                                   |
| Buffer    |                                   |
| Layer     | A collection of selected packages |
| Kill-ring |                                   |
|           |                                   |

## Functions

Function refers to the thing that you are calling when you hit a key or series of keys. For example j in normal modeis mapped to the function evil-next-line. In elisp these usually look like strings of hyphenated words. spc spc opens helm M-x and lets you search for functions by name and execute them. Note that functions may also be refered to as sexps (symbolic expressions).
## Buffers

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
## Major Modes

This is how emacs organizes important sets of functionality. Each buffer will have one major mode at a time. It can customize anything about emacs so that it suits the buffer you are working with. There is a mode for editing C#, a mode for editing latex, a mode for viewing files (dired-mode), a mode for searching (helm-major-mode), a mode for emulating a terminal (term-mode). You can see what major mode you are in at the bottom of each buffer in your mode line. Usually this is automatically set depending on which buffer you are in. Major modes specific functions are on the , key (also spc m).
## Minor Modes

Minor modes are smaller sets of custom behavior that can work together. A major mode will automatically set a bunch of relevant minor modes, but you can toggle them with spc t. For example spc t n toggles a minor mode for line numbers. You can hover over the symbols in the modeline with your mouse to see what minor mode each represents. spc h d m (help describe mode) opens a comprehensive list of your active minor modes. Move your cursor to one and hit enter to get more information.

Side Note: The information opens in a split buffer titled *help*. Many of these buffers that are meant to be temporary can be closed quickly with q.

## Layers

Everything so far (except specific key bindings) applies to emacs in general. Layers, however, are a spacemacs specific term. Layers are meant to be a simple way for you to customize your configuration by adding only one line to your .spacemacs file. See the list to see what are available. Check out the latex layer for example.


