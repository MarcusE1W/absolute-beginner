
+++
title = "Howl Editor"
date = "2018-07-17"
hide_authorbox = false
disable_comments = false
categories = ["Editor"]
tags = ["Howl"]
draft = true
+++

An introduction into very keyboard focused Howl editor

<!--more-->
# First thoughts

# Installation
The installation of the binary package in Archlinux is really easy.
```bash
trizen -S howl
```

Usefull commands and shortcuts

- Alt+x TAB for command palette
- alt-s for document structure
- Ctrl-g for document grep

# Define a custom Theme

Copy the template Theme

Provide styles for the lexer
TODO: What is the differnece in color definition with Xo and # ?

# Define a Lexer

A lexer describes the structure of a programming language and can then be used to support:
- syntax highlighting
- auto indent
- support the `buffer-structure` (alt-s)
- automatic insertion of pre defined code-blocks (snippets)
- a Inspector to mark syntax errors

A lexer is similar to other Howl bundles and is defined in some files:

- **init.moon** : Define the name link to other lexer files
- **xxx_lexer.moon** : define the structure of the programming language like keywords, functions, comments etc.
- **xxx_mode.moon** : Define indentation

Additionaly if you support an inspector this will be done in:
- **xxx_inspector.moon** : Define a function to show errors (optional)

(xxx stands for the name of the programming language you want to use)

The good news is that you do not have to know about Moonscript to write nice lexer for Howl. The lexer follows mostly a given structure that you can copy and then adjust to the language of your coice.

## xxx_lexer.moon
This file is the main part of the lexer to describe parts of the programming language structure.

The file itself covers differt parts of the language one by one.

### The minimal howl lexer.
To create a quick minimal lexer you could just describe keywords and maybe comments and strings because they are easy.

Every lexer starts with some

- keyword
- comment
- operator symbols


### additional great functions
- strings
- functions and modules

Note to P lexer document
Match styles in the Theme


## xxx_mode.moon
- Define 'buffer_structure' to use with 'Alt+s'
- Define Indent and unindent patters
- Define code blocks for automatic insertion after <RETURN>
    - First is the pattern to match the code block opening,
    - Second is the pattern to match the code block closing
    - Third is the code block closing text itself (not a pattern) for insertion
    - [Example in lua_mode.moon]( https://github.com/howl-editor/howl/blob/master/bundles/lua/lua_mode.moon#L42)
RegEx:
- Beginners [guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) to Regex
- [RegEx editor](https://regex101.com/) to try regexe and experiment

## init.moon

## Rest
- README
- misc/example




