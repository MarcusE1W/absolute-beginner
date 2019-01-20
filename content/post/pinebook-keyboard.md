
# Using the Pinebook with the keyboard (mainly) 
 
Principle approach
Meta: 	for DE
Ctrl: 	for Apps
Alt: 	for User and Extensions

Allow for common exceptions like Alt+TAB

The Pinebook is a great little Laptop. Except for the touchpad. The touchpad feels a bit unresponsive and unprecise. Also, ahve you noticed that you often do the same things with your mouse agia and again ? 
Start a programme, move the window, start another window move that as well, so that it is all visible and then work. Maybe start a third programme and so on.

So the suggestion is to use the keyboard a bit more to organise where your programme windows are on your display and to move between them.

There are probably many ways of doing that but here is my suggestion. My example is based on the desctop environment LXQt but this setup can be done in other desktop environments as well (KDE, Xfce)

There are two main ideas:
1. You use 4 different desktops. That means programms can be assigned to different desktoprs and be maximised without getting much in each others way.
2. If you have more than one programme running on one dektop or you only want to use one then there is a conveniet way to split the screen into half and place the windows next to each other.

In addition to that but not so important is to use regulary use the same desktop for tha same programms. e.g.

| Desktop | Programme |
| -----   | -----     |
| 1       | Terminal  |
| 2       | Browser   |
| 3       | Editor    |
| 4       | Work      |
That way you don't have to think much about on which desktop a programme is. All sorts of variations that fit your way of working are possible of course.

How does a workflow to open 3 programmes and work with them look like look in this scenario? 

1. switch to desktop 2 
2. open a browser, search some context and copy it
3. switch to desktop 4 and open LibreOffice, paste your content, maybe add some more.
4. switch to desktop 1 and open one terminal and start a system update
5. because you want a second terminal on this desctop you move this one to the left side of the screen
6. open another terminal, search for a configuration file and copy a paragraph from it.
7. switch to desktop 2, open a forum and paste your config.

All this could happen with no, or very little use of the mouse or touchpad.

Now keybindings exactly do you use ?

| Description               | Key                                                 |
| ---                       | ---                                                 |
| META + 1 (or 2 or 3 or 4) | Switch to desktop 1 (or 2 or 3 or 4)                |
| META + Space              | Start a programme with Runner, the LXQt app starter |
| META + Enter              | Start new Terminal                                  |
| META + Arrow Left         | Move window to the left half of the desktop         |
| META + Arrow Right        | Move window to the right half of the desktop        |
|                           |                                                     |

(Again, here are many ways to set the keybindings but these are partially borrowed from Windows (Meta-Left / Right) or other keyboard oriented window manager (META-1 (2/3/4) )

Shift META move window to another desktop and switch to that desktop

