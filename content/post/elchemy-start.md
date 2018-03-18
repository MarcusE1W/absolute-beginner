+++
title = "Elchemy for beginner"
date = "2017-12-07"
hide_authorbox = false
disable_comments = false
categories = ["Programming languages"]
tags = ["Ocaml"]
aliases = ["/post/all-grown-up/"]
draft = true
+++

ELchemy compiles code compatible with ELm to ELixir.

<!--more-->


# Intro

Elm on server compiled to Elixir.

This is a  [good](https://hackernoon.com/elmchemy-write-type-safe-elixir-code-with-elms-syntax-part-1-introduction-8968b76d721d) docu.


# Install Elchemy

Muehsam

Check if the install was correct:
```
elchemy version
```


# Getting started

Maybe create a folder for elchemy where you want to save all your elchemy code. Then create your first elchemy test
```
mix new test1

cd test1
```
This basically sets up an Elixir

TO add Elchemy in this folder use:
```
elchemy init
```

You will see something similar to this, depending on your elchemy version
> Found existing entry: /home/mmw/.mix/archives/elchemy-0.6.6
> Are you sure you want to replace it with "https://github.com/wende/elchemy/releases/download/0.6.6/elchemy-0.6.6.ez"? [Yn]
Type `y`

elchemy init will download some files and then complete with this info:

> Elchemy 0.6.6 initialised. Make sure to add:

>	**|> Code.eval_file("elchemy.exs").init**

> to your mix.exs file as the last line of the project() function.
> This pipes the project keyword list to the elchemy init function to configure some additional values.

As mentioned in the info, you have to open the file mix.exs in your current folder and edit it to add the marked line. If your editor of choice then the command is

`atom mix.exs`

Here find the last line of the project function `def project do`. That is the line after `]` and before `end`.

Here add `|> Code.eval_file("elchemy.exs").init` as mentioned above. The result should look like this:

```
]
|> Code.eval_file("elchemy.exs").init
end
```

Then run `mix test` to check if everything went fine. You probably will see some warnings, but there should be not errors.
