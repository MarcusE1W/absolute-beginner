+++
title = "Alice ML"
date = "2018-05-21"
hide_authorbox = false
disable_comments = false
categories = ["Programming languages"]
tags = ["Functional Programming", "SML"]
draft = true
+++

Alice a modern SML functional programming language with parallel programming support.

<!--more-->

# Alice installation on Archlinux

**NOTE: if your system is a 64bit only Linux, it will not work**
32Bit support needs to be installed

 - Alice [github](https://github.com/aliceml/aliceml)
 - The dependencies `smlnj smlnj-runtime ml-lex ml-lpt ml-yacc` seem not to be available on Archlinux.
 So as per the [SML/NJ website](https://www.smlnj.org/) you need to install the compiler manually.
     - Download `config.tgz`
     - move config.tgz in a now folder of choice, maybe called alice ?
     - unpack with `tar zxvf config.tgz`
     - you could edit the `config/targets` file, but use the standard
     - call `config/install.sh`, calling it from within the `config` folder won't work.
     - change vm-s../Makefile.csv
     - _and it does not work_
     - to be completed

 # Impression
 - It seems that there is no active development for Alice anymore.
 - Alice programms only run in a interpreted VM. That is not the fastest way to do thing and kind of spoils the fun of the parallel programming support.
 - Erlang shows that there is a use case, but..



