+++
title = "F# for beginner on ARM64 Linux"
date = "2020-11-04"
categories = ["Programming languages"]
tags = ["F-sharp"]
draft = true
+++



# Install with Manjaro (Archlinux)

Just install the dotnet binary AUR package. It also works for aarch64.

> sudo pacman -S dotnet-sdk-bin   

Create a file called `hello.fsx` that looks like this:

``` fsharp
printfn "Hello World from F#"
```

Now compile and run this F# script with the following command:

> dotnet fsi hello.fsx

If this is your first time using .NET Core, there will be a short, one-time message about using the .NET SDK. After that, you’ll see the following output in your console:

Hello World from F#

To create a project use

>dotnet new console --language F#
>dotnet run

You will see a message saying “Hello World from F#”.

# Helpful links
https://fsharp.org/


