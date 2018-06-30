+++
title = "Ocaml for beginner"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["Programming languages"]
tags = ["Ocaml"]
aliases = ["/post/all-grown-up/"]
draft = false
+++

Explore Ocaml, an functional programming language that is mayby not as strict as some others.

<!--more-->


# Intro

Ocaml is an interesting language and technic. However for the beginner it is not that easy to get your head around which tools to use.

There seems to be consensus that the package manager to use is `opam`. That makes at least the installation of the other tools easy once the preferred tool has been chosen.

Other things that need to be considered are (and this list is from the beginners view and probably not complete):

1. Standard Library
2. Build system
3. The editor
4. The interactive REPL (called toplevel in the Ocaml world)
5. Tutorials

##  The Standard Library
The standard library provides the most basic functions every developer needs from time to time like print, file handling and so on. You would be foriven to think that it beeing called the standard library it would be a clear thing and that's what to use.
Apparently the original Ocaml std. library seems to have a few design inconsistencies and gaps. This lead to the development to new "standard libraries".
A nice but not conclusise discussion about the best standard library can be found [here](https://www.reddit.com/r/ocaml/comments/665w26/which_standard_library_is_the_best/).

I have found  mostly these libraries discussed:
- the original one: with inconsistencies and gaps
- Batteries: A community driven effort to replace the original Std. Library.
- Core: A very comprehensive library but it comes as a big block and if you use one function you end up with the full library linked to your programm wich makes it unneccessary big.
- Containers: Community driven library to replace the Standard Library. It is an a bit newer effort compared to Batteries.
- [Base](https://github.com/janestreet/base) and Stdio: This has been developed based on the learning of the development of Core. The Base library is small and covers about the same as the original std. library with the exception that standard input - output is in a seperate library called 'Stdio'. The documentation for Base and Stdio is still improving. How Core and Base are related is a bit unclear to me.

I am sure all of these libraries are useful, and it is now for the beginner to decide what to use. Not ideal.

Based on gut feeling and a look on the documentation and which library has been downloaded how often from OPAM I will go with Base and Stdio.

##  The build system

The build system manages all dependencies that your programme might have and
There are tools available for Ocaml like: ocamlbuild and oasis, jenga, probably many others and jbuilder. To make it short I think the general advise is to use jbuilder for new projects. As a beginner that's a given, so jbuilder it is.

##  The editor
This text is not to give you advice which editor to use. Emacs, Vim, NeoVim, Spacemacs, Sublime text,  Atom  and VScode (plus more) seem all to be popular choices for   Ocaml.
If you don't have a choise already I fined the open source options Atom and VScode quite approchable.
The important bit as I see it is that the editor supports the Merlin Ocaml editor tool. Merlin provides essential functions for Ocaml editing that can be implemented by all editors.
The above mentioned editors all support Merlin more or less.
Merlin requires a description (.merlin file) of your programme in your project folder. It comes handy then that the build system jbuilder creates the .merlin file automatically.

##  Repl / toplevel
The Ocaml world the tool to interactively execute commands is called top level. In many other languages this tool is called REPL (R.. Execute P.. Loop). It tool is especiall tractiacal for learnig and is referred to in most tutorials. The standard REPL can be started with `ocaml`. Hoever most people reccomed an alternative REPL called `utop` and is is the most reccomended REPL.

# Ocaml installation on Archlinux

- install: opam
- install: rsync
- a package called gringo is needed, it is part of community package clingo
- follow this instructions: [link](https://github.com/realworldocaml/book/wiki/Installation-Instructions)
- install the repl: `opam install utop`
- run REPL utop the first time, remember to write ;; (really ? you ask, yes really) if something should be executed, exit utop with #quit;;


### Switch to another Ocaml version

`opam switch list` to see the availabe Ocaml versions
`opam switch set XXX` to switch to versioin XXX. if the version is not yet installed it will be installed.


## Ocaml tutorials for beginner

- RWO
- tryme
- Ocaml doc
