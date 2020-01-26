+++
title = "Spacemacs for beginner"
date = "2020-01-15"
disable_comments = false
categories = ["Editor"]
tags = ["Spacemacs", "Vim"]
draft = false 
+++

An introduction into the Spacemacs editor for a user with little Vim/Emacs experience.

<!--more-->


# Spacemacs for Beginner

Spacemacs is a beginner friendly extension of the very capable editor Emacs. One potential down-side for the beginner is that there is a lot of functionality available and you have to find out what is the most useful first. To help with this Spacemacs has a clever menu system that shows you the available functions and the necessary key strokes.

This text tries to give an introduction into spacemacs for someone who is not familiar with Vim or Emacs. 
After reading this you should be able to do some productive work with it.
The assumption is that you have installed Spacemacs with Evil (Vim) support.
Vim has some very powerful and sometimes very cryptic commands, only some of them will be covered in this text. 
Also the tables you see in the text only give you a selection of commands. 
The good news is that with Spacemacs you don't have to remember all commands but you can also use the Spacemacs menu (SPC).

[Also read the latest official Spacemacs beginner guide (Develop Version)](http://develop.spacemacs.org/doc/BEGINNERS_TUTORIAL.html)

## Executing commands in Spacemacs
The main way to execute commands is to press SPC (the space key) and then a combination of keys for the specific command. Once `SPC` has been pressed a menu opens that shows the possible keys. 
E.g. `SPC f s` saves the current buffer. 
It is probably worth just to try a few commands that look interesting to you. For your experiments maybe have a file available that you can load just for testing.

Double letters in the SPC menu usually are used for particular useful commands like SPC b b for the list of buffers or SPC f f to open a file . 

## Opening files
There are several ways to open a file, but a good start is the file selector Treemacs, activated with `SPC f t`.
Move to the Treemacs window with SPC 0 and back to the previous buffer with it's number `SPC <window number>`.

While using Treemacs:

| Function                                               | key               |
| ---                                                    | ---               |
| Show content of a sub-folder                           | RET (Return)      |
| Open file                                              | RET               |
| Rename a file.                                         | R (rename)        |
| Create a new file                                      | c f (create file) |
| To toggle between hiding and showing hidden (.) files. | t s               |


## Basic Spacemacs Evil (Vim) commands
There are (I am sure but have not made it that far yet) many useful vim commands to edit your text and work with the editor. I think as a beginner you don't need all of them. So here are some vim commands that are useful to have a good start and which are, I think also quite easy to remember.
The vim mode is a so called modal model. This means it has several different modes that are specialized in doing one thing especially good. The Spacemacs documentation describes this very [well](http://spacemacs.org/doc/DOCUMENTATION.html#states). 

Spacemacs also shows a different colour for the window number depending on your mode.

- Normal mode (ESC). This is where you execute vim commands and edit text, not to write text. To write text you switch to insert mode.
- Insert mode (i). Use insert mode to write text. some more basic text editing also works here.
- Visual mode (v/V) This is where you select text. Change to visual mode and select text. Then execute commands. You can execute vim commands like copy but you can also execute the SPC commands from spacemacs that are relevant for text selection.


Vim (and Spacemacs uses a Vim emulation) is famous for being a modal editor. That means basically it has one mode to write text called `insert mode` and some other modes to work with and format the text. Hence the name modal editor, there are several modes where different things happen like writing, editing, working with selections. 
The most important of these functional modes is `normal mode`. When you start Spacemacs it will be in normal mode first. You can see that parts of the mode line are yellow.

In normal mode you can use normal keys to execute commands, no need for Ctrl-this or that.
E.g. if you want tom copy the char under the cursor, you press `y` in normal mode. To inset what has been copied press `p`. If you want to select more than one character as you normally do, you enter visual mode with `v`, then mark the test to select and press `y` to copy your selection and again `p` to paste.

| function                                           | normal mode |
| ---                                                | ---         |
| enter visual mode for selections                   | v           |
| copy (yank) marked selection or char under cursor  | y           |
| paste (insert)                                     | p           |
| cut (delete) character under cursor                | x           |
| enter visual mode for whole line selections        | V           |
| enter insert mode to write text.                   | i           |
| leave insert mode to execute commands.             | ESC         |
| move (or select) to the beginning of the next word | w           |
| move (or select) to the end of the current word    | e           |

## Move cursor in the current buffer

| function            | normal mode | alternative     |
| ---                 | ---         | ---             |
| one character left  | h           | arrow-left      |
| one row down        | j           | arrow-down      |
| one row up          | k           | arrow-up        |
| one character right | l           | arrow-right     |
| one word right      | w           | Ctrl-arrow-left |
| one word left       | b           | Ctrl-arrow-left |

The idea behind the hjkl keys for cursor movement is that the hands have not to move from the base key line of your keyboard to move the cursor. The base row is the middle row of characters on your keyboard. This way your hands do not have to move around so much to reach the arrow-keys or the mouse. However,  you can also use the arrow keys.

- In insert mode the arrow keys, page-up, page-down, Home and End keys can be used.

### The clever editing bits ###

So what's all the hype about. so far the vim editor functions have made you switch between insert mode to enter text and normal mode to do some very basic editing.
Here now some more clever bits, and they benefit very much form the fact that you can use normal keys as commands in normal mode as opposed to Ctrl-this and Ctrl-that in other editors.

In Vim and spacemacs you can combine commands. E.g. 

**Text selection**

| function                               | keys |
| ---                                    | ---  |
| select the word under the cursor       | viw  |
| copy the word under the cursor         | yiw  |

`viw` changes to visual mode and selects the word currently under the cursor.
`yiw` is similar but yancs (copies) the word under the cursor. If you want to see what you copy you can also press `viwy`

**Text deletion**

| function                               | keys |
| ---                                    | ---  |
| cut the current line                   | dd   |
| cut and copy the word under the cursor | diw  |
| cut until next . (sentence end)        | df.  |

`diw` works similar to yiw. It deletes the word under the cursor.
`df.` is a clever bit. It deletes everything until it finds the next `.` You can search for other letters as well.

Mind you that all operations with `d` cut the text and don't just delete it. The current content of your standard clipboard will be overwritten.

**Add more space**
Often you want to add more text in your existing document and for that you need space. So here are some useful normal mode commands to add more space.

| function                              |   |
| ---                                   | ---   |
| add a new line over the current line  | [ SPC |
| add a new line under the current line | ] SPC |


### Mark/unmark lines as comments

| function                             | normal mode | spacemacs |
| ---                                  | ---         | ---       |
| mark (unmark) a selection as comment | gc          | SPC c l   |
| mark current line as comment         | gcc         | SPC c l   |

__Super bonus function to move in text__
A very nifty function to jump quickly to text currently displayed in the window is `SPC j j`.

1. After the second j of the SPC command select the first letter of the text where you want to jump to. So basically look at the word you want to jump to and select it's first letter.
2.  All the corresponding letters in the visible text of the window will be marked with a two letter combination.
3. Key in the two colourful letters of the position at the beginning of the word where you want to jump and there you are.
4. It is much more straight forward than it sounds. Try it.


## File handling

| function                                           | normal mode | Spacemacs |
| ---                                                | ---         | ---       |
| save                                               | :w          | SPC f s   |
| close buffer                                       | :q          | SPC b d   |
| save and close buffer                              | :wq         |           |


## Window handling
Windows are the text areas you see in Spacemacs. When you start it is usually one window. You can split the screen to see two or more windows at the same time.

Additionally spacemacs uses the term buffer. Every buffer is assigned to one file. You can have a large number of buffers open but only show a few in windows. Also spacemacs always has some internal buffers open like the `*Messages` buffer. 

To keep an overview there are several SPC commands to manage windows and buffer.

- To activate a specific window on your screen you can type `SPC <buffer-number>`

### Close a window or buffer
- `SPC w d` (window delete). This will close the currently active window. The buffer is still open but not visible and you can continue writing at a later time.
- `SPC b d` (buffer delete). This will close the buffer (file). That means either you have saved the text or you will be asked to save it and then it is closed. the window however will stay open and a different buffer will be shown in this window. Confusingly it can happen that the same buffer (file) is shown in two windows. In that case you probably don't need all the windows and you can close one with `SPC w d` or open another file in the second window.
- To close window and buffer at the same time you can use `SPC w x` or `SPC b x`

### Show a different buffer (file) in your current window.
- If you have several buffer (files) open and want to show a different buffer file in your current window then open the buffer selection screen (SPC b b) to jump to other open buffers (files)
- To switch back to the last buffer in the current window use `SPC TAB`

# Configuration
As mentioned in many places, configuration  in Spacemacs happens in the .spacemacs file. The .spacemacs file is largely split in 6 sections:


..... some comments at the top

1. `(defun dotspacemacs/layers ()`

2.  `Dotspacemacs-configuration-layers` ... add layers

3. `defun dotspacemacs/init` -- spacemacs config 
4. `(defun dotspacemacs/user-init ()` -- setup for the very start of emacs

5. `(defun dotspacemacs/user-config ()` -- personal user configuration

6. `(defun dotspacemacs/emacs-custom-settings ()` -- don't make changes

...... some stuff at the bottom

1. In the first section you find already predefined configuration functions with default settings. Not so important fo the beginner 
2. This is the important bit. Here you can add and remove layers. A core function of Spacemacs
3. Here are all sorts of parameter and switches for Spacemacs. You find a small description of what they do in the comments above.
4. Here you can put settings for the start of Spacemacs. If in doubt use section 5 though.
5. User settings. Small pieces of code similar to the standards settings in sections 3 to set parameter for Spacemacs.
6. Don't use


### Add and remove layers (packages)

Hit `SPC f e d` (file emacs dotfile) to open the .spacemacs file. This is where you can customize everything. 

Find the `dotspacemacs-configuration-layers` line. 

To add latex into the layer list it should look like this:

```elisp
dotspacemacs-configuration-layers '(
latex
other-layer
other-layer
)
```

Now spacemacs will load that layer on startup for you, which includes a major mode for editing latex and a bunch of commands. You can now either restart emacs, or hit `spc f e R` (file emacs reload) to reload your config. Now if you hit `SPC f f`  (file find) and open a latex file you should have some syntax highlighting and latex specific commands.

NOTE: the whole large section of standard configuration is called `(defun dotspacemacs/layers ()` whereas the small paragraph where you add your own selection of layers is called `dotspacemacs-configuration-layers`.

If you make changes, save with `SPC f s` and restart with `SPC q R`.

[Good docu how to customise Spacemacs](https://medium.com/@jaysoifer/customizing-spacemacs-e9013bb18933)

# Beginner friendly key-bindings

Vim's normal mode has some very powerful editing tool, but if you are used to the key-bindings that are very common on most GUI's and you only use Spacemacs occasionally then you might wish to use the common key-bindings in Spacemacs as well.

One nice solution could be to use GUI (common) keybindings in insert-mode and vim commands in normal mode.

There is one solution for this.

PhilipDaniels created [windows_default - mode](https://github.com/PhilipDaniels/windows-defaults)

For installation please read the description in the repository. This layer defines many useful keybindings, so it is worth to read the complete README.

# Useful links:

- An absolute beginners guide to Spacemacs for academic [writing](https://ontologicalblog.com/2016/10/14/an-absolute-beginners-guide-to-spacemacs-for-academic-writing/)
- Great [introduction](https://practicalli.github.io/spacemacs/documentation/) into Spacemacs with additional info about Clojure and Cider.

