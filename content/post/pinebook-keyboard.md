+++
title = "Pinebook keyboard first"
date = "2019-02-19"
hide_authorbox = false
disable_comments = false
categories = ["Pinebook", "Keyboard"]
tags = ["LXQt"]
draft = true
+++

How to use the the Pinebook with Manjaro LXQt and a keyboard first approach ?

<!--more-->

# A keyboard first approach to use Manajro LXQt


The Pinebook is a great little Laptop. Except for the touchpad. 
The touchpad feels a bit unresponsive and imprecise, to say it nicely. 
Also, have you noticed that you often do the same things with your mouse again and again ?
Start a programme, move the window, start another window move that as well so that it is all visible and then do some work. Maybe start a third programme and so on.
after a while your display has a lot of windows open and might looka bit like this.
[Pic of display with three overlapping windows]


You can tidy that up with the mouse a bit and maybe it looks like this?
[Pic of the three windows, not overlapping]

The truth is that there is only so much space on one laptop screen so arrangements with more than two or three windows are probably a bit messy. Also the effort to move the windows around with the mouse on the screen might be a bit much. 

So the suggestion is to use the keyboard a bit more to organise where your programme windows are on your display and to move around  between them. 
As this are always the same activities you would also use the keyboard in the same way again and again and by that, so is the idea learn this rather quickly. 
Also, this text is not about doing everything with the keyboard, just some reoccuring basic things.

To do so some keyboard shortcuts have to be defined. 
As it so happens that has kindly already been done in the Pinebook Manjaro ARM LXQt release. 
So if you want to try it, you can copy this distro to an SD card and follow this guide but this setup is also possible in  other desktop environments like (KDE, Xfce, ..). 
However some setup is required for the full

**Here is the  main idea:**

1. If you have more than one programme running on one dektop or you only want to use one desktop then there is a conveniet way to split the screen into half and place the windows next to each other.

2. You use 4 different desktops instead of having all programms open in one window.  That means programms can be assigned to different desktoprs and be maximised without getting much in each others way. Hey, you say, that has nothing to do with mose or keyboard usage. Correct, but bare with me..

## Moving windows around with the keyboard

As the desktop of the pinebook is widescreen it is actually quite usefull to splitt the screen and show two programms next to ecah other.
[Something like this:](images/splitt-screen1.png)
The shortcuts for that are easy:




## Using more than one desktop.

The problem is, once a desktop is full with windows, however cleverly arranged, it's full.
One option is to minimise and maximise the window and then switch between them and that works.
A second way and I feel a bit more practical is to use more than one desktop ands then use keyboard shortcuts to switch between them quickly.

So how to do that ?
Rather than place all windows on one desktop you use, let's say four. A second desktop looks like the first, just initially empty again before you start a programme. All initially started programms on desktop 1 are still there and one klick (or keyboard shortcut away).
[pic showing three apps on one desktop and then two desktops first, two apps next ot each other and a second desktop with a full screen firefox]


Now you can start the second descktop just like the first and arrange windows if required. Or use a third desktop or a fourth. On thing that works well is to have your applications maximised on each desktop and therefore less need to arrange windows in the first place.



## More fine tuning of the approach

In addition to multiple desktops you can assign certain desktops to be used with specific desktops. That way you don't have to think too much abouth where's what.

Eg. I have the terminal and maybe settings always on Desktop 1 and Firefox always maximised on Desktop 2. The other desktops I use a bit more freely but here is a pattern that works for me:


| Desktop | Programme |
| -----   | -----     |
| 1       | Terminal  System |
| 2       | Browser   |
| 3       | Editor    |
| 4       | Other work      |
That way you don't have to think much about on which desktop a programme is. All sorts of variations that fit your way of working are possible of course.




## Make it more consistent.

One more thing.

At the beginning it was said that it should be easy to remember the keyboard shortcuts and all considered, the sortcuts used here are all a bit over the place.

There is no ready made way to solve that as many programms and desktop environments or termianls have shortcut and they are all over the place.

That said here is a way to splitt the available shortcut keys like META, Alt and Ctrl and try to get some cnosistency.

Principle approach

- **Meta:** 	for Desktop environments
- **Ctrl:** 	for Programmes
- **Alt:**	 	for User and Extensions

An useful expecption Alt+TAB as this is just a very well known shortcut

META 1/2/3/4 to activate desktop/workspace
Shift META move window to another desktop and switch to that desktop
META-Space - Start programme with Runner, the LXQt app starter
META-Enter - Start new Terminal


## Starting common apps with the keyboard.

So now that moving windows around is nicely sorted, the other activity that is very common is starting applications.
Everyone has their own important applications so here is a suggestion to focus on the essential:

1. a shortcut to start the termian (of your choice)
2. a shortcut to start any programme
3. a shortcut to start the Settings

This is all very driven by your personal preference, but I feel it's a good basis. You might want to add other applications.

| Description | Key |
| --- | --- |
| start the terminal |


## It's all coming together

How does a workflow to open 3 programmes and work with them look like look with this brand new approach?

Start your freshly customized Desktop Environment
start a terminal, update manjaro, or so
start some settings, move the settings window to the left of the desktop
switch to the termianl app

switch to desktop 2
open a browser, search some context and copy it
switch to desktop 4 and open LibreOffice, paste your content, maybe add some more.
switch to desktop 1 and open one terminal and start a system update
because you want a second terminal on this desctop you move this one to the left side of the screen
open another terminal, search for a configuration file and copy a paragraph from it.
switch to desktop 2, open a forum and paste your config.

All this could happen with no, or very little use of the mouse or touchpad.

## List of standard shortcuts in Pinebook Manjaro LXQt

.
.
.
