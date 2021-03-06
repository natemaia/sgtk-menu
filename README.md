# sgtk-menu
This project is an attempt to create a launcher, that behaves decently on **sway**, but also on **i3** window manager. 
It may also be used in some **floating WMs**, but I only use **Openbox**, and don't test it elsewhere.

**sgtk-menu uses `pygobject` to create a themeable, searchable, gtk3-based system menu w/ some optional features:**

- `.desktop` entries-based system menu;
- search box to find what you need quickly;
- favourites (most frequently used entries) menu above (optional `[-f | -fn FN]` argument);
- user-defined menu below (optional `[-a | -af AF]` argument);
- `sgtk-dmenu` command: search and run commands in `$PATH`;
- `sgtk-bar` command: user-defined horizontal or vertical button bar;
- `sgtk-grid` command: a GNOME-like application grid.

Read [wiki](https://github.com/nwg-piotr/sgtk-menu/wiki) for more information. 
See [screenshots](https://github.com/nwg-piotr/sgtk-menu/tree/master/screenshots) 
for usage examples.

### System menu w/ favourites above and custom appendix below

![screenshot](http://nwg.pl/Lychee/uploads/big/ac538b60c3f32c36b689049cb0172863.png)
*The menu in Adwaita-dark GTK theme w/ Aqatix icons*

### Horizontal button bar as the Exit menu

![screenshot](http://nwg.pl/Lychee/uploads/big/e2d600d32e4bc0c8458fbe85c8428853.png)

### sgtk-dmenu

![screenshot](http://nwg.pl/Lychee/uploads/big/8397695512a2d655199f95db683060f8.png)

### sgtk-grid

![screenshot](http://nwg.pl/Lychee/uploads/big/5a00ddd6dbf4cd27a5eb088f8d3f8444.png)

## Background

Well, I didn't even think that sway needed a menu, being happy with [wofi](https://hg.sr.ht/~scoopta/wofi) and 
[dmenu-wayland](https://github.com/nyyManni/dmenu-wayland). I started coding just to find out what the 
[Desktop Menu Specification](https://specifications.freedesktop.org/menu-spec/latest) looks like, and also to learn some 
more [pygobject](https://pygobject.readthedocs.io/en/latest). The best menu I know, however, does not (yet?) behave well 
on sway. So, I thought to share the code, which has already taken me more time that I had ever expected.

[This code](https://github.com/johanmalm/jgmenu/blob/master/contrib/pmenu/jgmenu-pmenu.py) by 
[Johan Malm](https://github.com/johanmalm) helped me understand how to make use of `.desktop` entries. Many thanks!

## How it works on sway

The problem to resolve is, that the Gtk.Menu class behaves differently / unexpectedly when open over Wayland and X11 windows. 
To work it around, the script opens the menu over a (semi-)transparent, floating window, that covers all the screen.

## i3 support, floating WMs support

Even if there exist plenty of good X11 menus, with the most excellent [jgmenu](https://github.com/johanmalm/jgmenu) 
on top, I'm doing my best to make sgtk-menu i3-compatible. It's also possible to use sgtk-menu in some floating window 
managers, e.g. to replace the Openbox / Fluxbox menu. 
See [wiki/Launching](https://github.com/nwg-piotr/sgtk-menu/wiki/Installation#launching) for details. 

## TODO
- On next sway / GTK release, check if the overflowed menus issue on sway is fixed; remove 50 SLOC long workaround if so.
