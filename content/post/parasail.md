---
title: "Parasail"
date: 2021-02-16T22:28:57Z
categories: ["XX"]
tags: ["Parasail"]
draft: true
---

How to start with ParaSail on Pinebook Pro

<!--more-->

# Install

## Prep

An Ada compiler is required. Good Ada support on the PBP is found in Ubuntu and
Debian. I used Armbian.

Also required:
````
sudo apt install libgtk2.0-dev
sudo apt install tcsh
```

Download zip
[link](http://parasail-lang.org/)

unzip

cd parasail...

```
make build_no_gtk
```

# First test

> This is taken from the `parasail_release_notes.txt`:

----------------------------------------------------------

You can test the installation by "cd examples" and then:

   % ../bin/interp.csh drinking_phils.psl

Program should produce:

   ParaSail Interpreter and Virtual Machine Revision: 8.x
   ...
   Parsing <install-dir>/lib/aaa.psi
   Parsing <install-dir>/lib/reflection.psi
   Parsing <install-dir>/lib/reflection.psl
   Parsing <install-dir>/lib/reflection.psi
   Parsing <install-dir>/lib/reflection.psl
   Parsing <install-dir>/lib/psvm_debugging.psl
   Parsing <install-dir>/lib/debugger_console.psl
   Parsing drinking_phils.psl
   ---- Beginning semantic analysis ----
   Starting up thread servers
    165 trees in library.
   Done with First pass.
   ...
   Finishing type descriptors.

   Command to execute:

You can then type: Test_DP 13

Program should produce, approximately:

   Party will go for 13.0 seconds.
    Initializing Used_Bottles for Phil null with 2
    Initializing Used_Bottles for Phil null with 1
    Initializing Used_Bottles for Phil null with 1
    Initializing Used_Bottles for Phil null with 1
    Initializing Used_Bottles for Phil null with 0
   Philosopher 5 arrives, with a taste for 1 5, and sits in front of 5.
   Philosopher 5 is thinking for 5 seconds
   Philosopher 2 arrives, with a taste for 2 3, and sits in front of 3.
   Philosopher 2 is thinking for 4 seconds
   Philosopher 1 arrives, with a taste for 1 2, and sits in front of 1 2.
   ...
   Philosopher 1 is drinking for 8 seconds
   Philosopher 2 is thinking for 2 seconds
    Bottle 3 about to be removed from Used_Bottles (1) of Phil 2
    Bottle 3 borrowed from Philosopher 2
    Bottle 3 now available to Philosopher 3
   Drinking Party is over
   Command to execute:

And then you can type: quit

---------------------------------------------------------------------

