 Kdapta-gtk-theme
======

A custom fork of the [Adapta theme](https://github.com/adapta-project/adapta-gtk-theme).

I like my themes dark. Very dark. This is why I forked Adapta to create my custom version with a much darker dark version.

Before using Kdapta
-------------------
*Please follow the instructions from the [official Adapta repository](https://github.com/adapta-project/adapta-gtk-theme).*

Required Components
-------------------
Kdapta supports Gtk+ 3.24.x, 3.22.x and 3.20.x

 ```
 * Gtk+-3.0             >= 3.20.0
 * Gtk+-2.0             >= 2.24.30
 * gtk2-engines-pixbuf  >= 2.24.30
 * gtk2-engines-murrine >= 0.98.1
 ```

Supported Desktop Environments
------------------------------

 ```
 * GNOME-Shell     >= 3.20.0
 * GNOME-Flashback >= 3.20
 * Budgie-Desktop  >= 10.4
 * Cinnamon        >= 3.2.0
 * XFce4           >= 4.12.2
 * Mate            >= 1.14.0
 * LXDE            >= 0.99.1 (Gtk+ 2.x only)
 ```

Unsupported Gtk+ Based Desktop(s)
-------------------------------
 * Pantheon
 * Unity7

 > **Note:**
 >
 >   * Kdapta does NOT support elementaryOS.

Installation from Git Source
----------------------------
1. If previous versions were installed/existed, remove them first.

 ```
 sudo rm -rf /usr/share/themes/{Kdapta,Kdapta-Eta,Kdapta-Nokto,Kdapta-Nokto-Eta}
 rm -rf ~/.local/share/themes/{Kdapta,Kdapta-Eta,Kdapta-Nokto,Kdapta-Nokto-Eta}
 rm -rf ~/.themes/{Kdapta,Kdapta-Eta,Kdapta-Nokto,Kdapta-Nokto-Eta}
 ```

2. Check build-requirements:
 Currently Kdapta bundles neither pre-generated stylesheets nor PNG images.
 So users and/or contributors should generate proper CSSs, PNGs and gresources at build-time.

 ```
 * autoconf
 * automake
 * inkscape                                  >= 0.91
 * libgdk-pixbuf2.0-dev (gdk-pixbuf2-devel)  >= 2.32.2
 * libglib2.0-dev (glib2-devel)              >= 2.48.0
 * libxml2-utils (libxml2)
 * pkg-config (pkgconfig)
 * sassc                                     >= 3.3

 * parallel                                  (if --enable-parallel)
 ```

 > **Note:**
 >
 >   * In OpenSUSE, add an extra dependency:
 >
 >     ```
 >     gdk-pixbuf-devel        >= 2.32.2
 >     ```
 >
 >   * Kdapta employs **SassC** wrapper of `libsass` to generate CSS stylesheets.
 >   * Kdapta uses `inkscape` to generate installable PNG files.
 >   * Kdapta uses `glib-compile-resources` to compile the gresource files for Gtk+ and Gnome-Shell.
 >   * `glib-2.0 >= 2.53`, Gnome-Shell 3.26 theming is used if `--enable-gnome`.

3. Build and install system-wide:

 ```
 ./autogen.sh --prefix=/usr
 make
 sudo make install
 ```

 > **Note:**
 >
 >   * Default prefix is `/usr/local`.
 >   * All 4 variants are installed by default.
 >   * `make` generates proper CSSs and PNGs to be installed.
 >     It will take about 5min to 15min to build.
 >     For example, Ubuntu's build-server takes 10min.
 >   * `sudo make install` installs multiple versioned theme and Gtk+ automatically selects the properly versioned one when running.

4. To speed up by using concurrency-build, pass this specific option to `autogen.sh`:

 ```
 --enable-parallel       enable parallel-build support (type: bool)
 ```

 > **Note:**
 >
 >   * This feature requires GNU `parallel`, so please add `parallel` to build-requirements.
 >     Parallel can execute multiple scripts and binaries to be suitable for multi-threading.
 >     It could especially shorten the rendering-time via `inkscape`.
 >   * `-jN` option to be passed to GNU `make` is surely usable, but Kdapta currently employs `parallel`.
 >   * This feature should not be applied when packaging on remote/shared build-servers.

5. To disable some DE supports, pass these specific options to `autogen.sh`:

 ```
 --disable-gnome         disable gnome-shell support (type: bool)
 --disable-cinnamon      disable cinnamon support (type: bool)
 --disable-flashback     disable flashback support (type: bool)
 --disable-xfce          disable xfce support (type: bool)
 --disable-mate          disable mate support (type: bool)
 --disable-openbox       disable openbox support (type: bool)
 ```

 > **Note:**
 >
 >   * The installer installs Budgie-Desktop support even if all of options above were applied.
 >   * Cinnamon/Mate support hooks `metacity-1` directory even if GNOME-Flashback support was disabled.

6. To enable extra Gtk+ release support, pass these options:

 ```
 --enable-gtk_next      enable Gtk+ 4.0 support (type: bool)
 ```

7. To change the default 4 **Key-Colors**, pass these options:

 ```
 --with-selection_color        Primary color for 'selected-items' (Default: #00BCD4 = Cyan500, type: string)
 --with-accent_color           Secondary color for notifications and OSDs (Default: #4DB6AC = Teal300, type: string)
 --with-suggestion_color       Secondary color for 'suggested' buttons (Default: #009688 = Teal500, type: string)
 --with-destruction_color      Tertiary color for 'destructive' buttons (Default: #FF5252 = RedA200, type: string)
 ```

 > **Note:**
 >
 >   * Color-codes are defined as `#` + 6-digit `HEX`s (Standard RGB definitions in HTML codes).
 >     Uppercases are strongly recommended in Kdapta code-base.
 >   * The Material Design Color Palette can be found [**here**](https://www.google.com/design/spec/style/color.html#color-color-palette).
 >   * Example: If you would like to use 'Teal500' as selection_color, use this:
 >
 >     ```./autogen.sh --with-selection_color=#009688```
 >
 >     This switchese the theme to almost Teal key colors.
 >   * Basically `selection_color` and `suggestion_color` should use `500` colors,
 >     and `accent_color` should use `300` colors.
 >   * While doing `make`, Kdapta changes those 4 colors in all stylesheets and images,
 >     and `make clean` cleans up all generated files from source directories.
 >   * This feature unfortunately is not supported in `Openbox-3` and `Telegram 1.0` theming.


Public License
--------------
 GPLv2.0

 > **Note:**
 >
 > SVG files are licensed under CC BY-SA 4.0.
 > And an icon-theme in Cinnamon thumbnails:
 > [**Paper Icons**](http://snwh.org/paper/icons) by Sam Hewitt is licensed under CC-SA-4.0.

Special Thanks to
--------------
 [Adapta](https://github.com/adapta-project/adapta-gtk-theme), the theme this theme is based on. 
 Nana-4, the developer of Materia (formerly Flat-Plat).

 And all supporters, thank you.
