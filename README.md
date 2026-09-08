# Wallpapers

A personal collection of wallpapers, plus a small CLI to set them as your background via [awww](https://codeberg.org/LGFae/awww), with animated transitions between changes.

## Gallery

Browse the full collection with thumbnails: **[GALLERY.md](GALLERY.md)**

The gallery is regenerated automatically whenever images under `walls/` change (see [`.github/workflows/gallery.yml`](.github/workflows/gallery.yml)).

## Usage

```
./wallpaper [-m mode] [-r <dir>] [-t <seconds>] [-T <transition>] [-d <seconds>] [-k] [<image>]
  -m mode      fill|fit|stretch|center (default: fill)
  -r <dir>     rotate through random images from directory (recursive)
  -t <seconds> rotation interval (default: 60; <= 0 disables rotation, sets once)
  -T <type>    transition: fade|simple|wipe|wave|grow|outer|center|any|random|none (default: fade)
  -d <seconds> transition duration in seconds (default: 1)
  -k           stop any running rotation and exit
  <image>      path to image file
```

With `-r`, a random image is set immediately, then a background loop swaps in a new
random image from that directory every `-t` seconds (default 60) until you run
`./wallpaper` again. Pass `-t 0` (or any value `<= 0`) to just set one random image
without starting the rotation loop. Each change fades in over `-d` seconds via the
`awww` daemon instead of a hard cut.

Only one rotation loop ever runs at a time: each invocation stops whatever loop is
already running (tracked via a pidfile) before starting its own, and the switch is
protected by a lock so two invocations firing at once (e.g. an autostart hook racing
a keybind press) can't both leave a loop behind.

Examples:

```
./wallpaper -r walls                    # random wallpaper, rotating every 60s
./wallpaper -r walls -t 300             # rotate every 5 minutes
./wallpaper -r walls -t 0               # single random wallpaper, no rotation
./wallpaper -r walls -T wipe -d 2       # rotate with a 2s wipe transition
./wallpaper -m fit some.jpg             # set a specific image with a given mode
./wallpaper -k                          # stop rotation
```
