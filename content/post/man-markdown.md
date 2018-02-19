+++
title = "Creating a man page from markdown with pandoc"
date = "2018-02-19"
hide_authorbox = true
disable_comments = false
categories = ["Development"]
tags = ["man pages", "markdown"]
aliases = ["/post/all-grown-up/"]
draft = false
+++

How to create a man page from a README.md file

<!--more-->
# Create a (unix) man page with Markdown using pandoc

Man pages are application documentation that you find for almost every Unix/BSD/.. system. The format is text based on a markup language called `Nroff`. The principle concept is similar to Markdown, however the markup language `nroff` is a quite a bit less readable than markdown.
Often variations of the `nroff` format are used like `groff`.

Man pages are usually used in a terminal. So if you want to see the documentation for the command `ls` (list files) then you can key in:
```
man ls
```
and you will see the available options for `ls`. This works for almost every programme, provided the programme author has written a page.


This tutorial describes how to create man documentation pages from a markdown file using `pandoc`

# Using pandoc

`Pandoc` is a text conversion tool that can convert text from markdown (or GitHub flavoured markdown ) to `groff`, a format that is used by the `man` command to show documentation.

## Installation of pandoc

As pandoc is often not installed as a standard tool you first have to install it on your system.

### Installation for Archlinux
```
pacman -S pandoc
```
Note: The above command installs quite a lot of dependencies. This is because it uses many shared files from Haskell (the programming language pandoc is build with). If you don't have use for haskell otherwise there is a pandoc version on the AUR called XXXXXXX that does not have these dependencies.

## Create a man page with pandoc

To create a man page from markdown we need a markdown file first.
Here is an example to start with:
```
# Header 1

Text for this `man** page

## Header 2

**bold text**

The last line
```

Save this file as `test.md`

To convert this file into a man page format use this command in the folder where `test.md` is saved:
```
pandoc --standalone --from gfm --to man test.md --output test.1
```

The result is in the file `test.1` and you can look at the new formal with `less test.1`.
This format is not how the man page will be shown. To see how your new file looks like as a man page, use:
```
man -l test.1
```

Let's have a quick look at the options of the `pandoc` command and what they do:

--- standalone: creates a complete man page, with complete structure

--- from: the format to convert from. In this example `gfm` (GitHub flavoured markdown) has been specified, but you can also write `markdown`. for the small differences see the [Pandoc documentation](https://pandoc.org/)

--- to: this is the format we want to concert the text to. In this case a man page

--- output: the name of the output file. You could also leave this out, then the output goes to `stdout`.

# Structure of a man page
Now that we can convert markdown to man pages it is worth mentioning that man pages often follow a certain structure. This makes it easier to find information.
Of course before you don't publish a man page you can also follow your own structure.

There are many header sections, that can be used. Only NAME is seen as mandatory.

NAME - The name and a short description of the programme 
SYNOPSIS - A short summary how to use the programme. e.g.: `pandoc [options] [input-file]...`
DESCRIPTION - Description of the programme 
OPTIONS - description of options
RETURN VALUE - return values of programme once it terminates 
EXAMPLES - always good to give some examples 
NOTES - Additional info 
SEE ALSO - reference to other related programmes
AUTHOR - as in author of the programme
HISTORY - of the programme if that is helpful

It is absolutely fine to use only some of these headers like for example: NAME, SYNOPSIS, OPTIONS or any other combination. Remember that NAME is expected.

# Creating a man page from a GitHub README.md

If you have a README.md in for example GitHub that explains your programme reasonably well you could use that file to create your man page. All you have to do is to add the above headers in the decisive places and the convert the updated file into a man page.
```
pandoc --standalone --from gfm --to man README.md --output prog.1
```

You might have already noticed the unusual naming convention to end the man page with `.1`. The number classifies your man page and `.1` stands for general.

