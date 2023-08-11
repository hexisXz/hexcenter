# Hexcenter

a store i forked because i hate the ubuntu store.

![AppCenter Screenshot](data/screenshot.png?raw=true)

## Building, Testing, and Installation

You'll need to run the following command to install all of the dependencies: 

``` sh
sudo apt install gettext libappstream-dev libflatpak-dev libgee-0.8-dev libgranite-dev libgtk-3-dev libhandy-1-dev libjson-glib-dev libpackagekit-glib2-dev libpolkit-gobject-1-dev libsoup2.4-dev libxml2-dev libxml2-utils meson valac
```

Run this command to build and install the appcenter 

``` sh
git clone https://github.com/hexisXz/hexcenter.git && cd hexcenter && meson build --prefix=/usr && cd build && ninja && sudo ninja install
```

To run hexcenter execute `io.elementary.appcenter`

``` sh
io.elementary.appcenter
```

if you want to uninstall hexcenter make sure you are in the build dir and run 

``` sh
ninja uninstall && sudo ninja uninstall && cd .. && sudo rm -r ../hexcenter
```      

## Debugging

See debug messages:
As specified in the [GLib documentation](https://developer.gnome.org/glib/stable/glib-running.html)

    G_MESSAGES_DEBUG=all io.elementary.appcenter

Show restart required messaging:

    sudo touch /var/run/reboot-required

Hide restart required messaging:

    sudo rm /var/run/reboot-required

Fake updates with the `-f` flag followed by PackageKit package name, **not** appstream id:

    io.elementary.appcenter -f inkscape

Load and preview a local AppStream XML metadata file, your local metadata will show up in the featured banner and will also be searchable. Metadata loaded this way will have a `(local)` suffix in it's name.

    io.elementary.appcenter --load-local /path/to/file.appdata.xml
