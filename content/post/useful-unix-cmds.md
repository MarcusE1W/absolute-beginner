+++
title = "Useful and amusing unix commands"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["System"]
tags = ["Shell"]
aliases = ["/post/all-grown-up/"]
draft = false
+++

Some helpful or interesting unix commands

<!--more-->



### cal			create a calendar**

`cal -3` shows three month
`cal -n 5` shows 5 month

### exa:			ls replacement**
For a nice ls -l replacement use

```
exa -l --header --binary  --git
```

`-l` or `--long` lists the file in a long version like command ls
`--header` or `-h` writes a header column as the first line
`--binary` or `-b` gives the size of the file
`--git` shows the git status

works well as a alias for `ll`

### cowsay		let the cow say something
`cowsay`

### cowfortune	cow gives fortune
`cowfortune`

### asciiquarium 	aquarium
Aquarium, with fish and castle
`asciiquarium`

### find a file
`find / -iname "file-name"`


