# fcitx-gtk3-sway-window-pos

Fix fcitx candidate panel position in swaywm

## Why

Wayland has no way to obtain window position

## How

Use `swaymsg -t get_tree` to get position

## Details

Path name in patch file is gtk2, but this is for gtk3. In fcitx source gtk3 files are links to gtk2 ones and use some ifdef to do gtk3 stuff.

## Why this is dirty

* Uses popen to call swaymsg instead of connecting the ipc
* Depends on jq for json parsing
* Queries focused window. I'm not sure this is always the right one.

## Why don't make it clean

* I'm too lazy
* This solution is only for swaywm
* Wayland has a extension protocol for im
