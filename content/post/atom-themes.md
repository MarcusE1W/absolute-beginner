
+++
title = "How to create Atom themes"
date = "2018-04-03"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Atom"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

How to create Atom themes without programming knowledge.

<!--more-->

# Intro
This is a tutorial to create Atom editor UI and syntax themes.
Any programming language is not required.

# UI
Start with suggested starter theme or copy any other

- file structure, what's defined where
- Colours
- Tab header
- File changed  symbol
- scrollbars
- Treeview header
- status bar hight
- Dynamic colours and hight adjustments in OneDark
- turn the drag bars on/off

# Syntax

Copy OneDark
- file structure, what's defined where
- Change background colour
- change colours
- Gutter
## lines
in `editor.less` or
```
.line {
```

### Editor-mini

atom-text-editor[mini]

  color: #d9d7ca;
  background-color: #797171;

TODO: find atom-text-in project (Ctrl-Shift-F)
  - the colour could be chnaged to the one of the editor, how does that look ?

# General
- package.json
  - set up "theme"
- publish picture for readme
- file `index.less`
- How to set up settings
