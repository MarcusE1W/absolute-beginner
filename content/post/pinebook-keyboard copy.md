
# A keyboard first approach to use Manajro LXQt


The Pinebook is a great little Laptop. Except for the touchpad. The touchpad feels a bit unresponsive and unprecise, to say it nicely. Also, have you also noticed that you often do the same things with your mouse agia and again ?
Start a programme, move the window, start another window move that as well, so that it is all visible and then work. Maybe start a third programme and so on.

So the suggestion is to use the keyboard a bit more to organise where your programme windows are on your display and to move around  between them. As this are always the same activities you would also use the keyboard in the same way again and again and by that, so is the idea learn this rather quickly. Also, this text is not about doing everything with the keyboard and some shortcuts, just some reoccuring basic things.

To do so some shortcuts have to be defined. As it so happens that has kindly already been done  in the Pinebook Manjaro ARM LXQt release. So if you want to try it, you can copy this distro to an SD card and follow this guide but this setup is also possible in  other desktop environments like (KDE, Xfce, ..). However some setup might be required.

Here is the  main idea:
1. You use 4 different desktops instead of having all programms open in one window.  That means programms can be assigned to different desktoprs and be maximised without getting much in each others way.
2. If you have more than one programme running on one dektop or you only want to use one then there is a conveniet way to split the screen into half and place the windows next to each other.

In addition to that but not so important is to use regulary use the same desktop for tha same programms. e.g.


 the META key (between Fn and Alt) will be used for all windows manipulation.

One exception can be  Alt+TAB as this is a well established key combination.


| Desktop | Programme |
| -----   | -----     |
| 1       | Terminal / System |
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

Principle approach
META key: 	for the desktop environment
Ctrl key: 	for apps
Alt key: 	for user defined shortcuts and extensions


| Description               | Key                                                 |
| ---                       | ---                                                 |
| META + 1 (or 2 or 3 or 4) | Switch to desktop 1 (or 2 or 3 or 4)                |
| META + Space              | Start a programme with Runner, the LXQt app starter |
| META + Enter              | Start new Terminal                                  |
| META + Arrow Left         | Move window to the left half of the desktop         |
| META + Arrow Right        | Move window to the right half of the desktop        |
| Shift META + 1 (or 2 or 3 or 4) | Move window to another desktop and switch to that desktop   |



