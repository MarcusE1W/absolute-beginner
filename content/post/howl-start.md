
+++
title = "Howl Editor"
date = "2018-07-17"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Howl"]
draft = true
+++

An introduction into the very keyboard focused Howl editor

<!--more-->
# First thoughts

# Installation
The installation of the binary package in Archlinux is really easy.
```bash
trizen -S howl
```


# Config
Everyone has different expectations for a standard config. These examples rreflect my own preferences. Many more things can be configured in many different ways.

Ctrl+q

howl.config.popup_menu_accept_key = 'tab'



# Define a custom Theme

Note: to see the default themes in action, have a look at the theme selector in the documentation. All the examples can be seen with different themes. The selector is on the top right of every docu page

Copy the Eastend template Theme

Define a list of your own colours and add them to the top.
then just link the new colors to the already defined ones.

# Define lexer for a programming language

The 'styles:' definitions in the theme can be used to connect themes and lexer.

All the definitions in the upper part get listed in the 'any' table at the bottom.

By leaving thing out of the 'any' table parts can be turned on and off

[Docu for Textadept LPEG lexing](https://foicica.com/textadept/api.html#lexer)

[Video for LPeg](https://vimeo.com/1485123)

[Lua LPeg docu](http://www.inf.puc-rio.br/~roberto/lpeg/lpeg.html)

## c( xxx, yyy) structure


## Definition of Identifier


