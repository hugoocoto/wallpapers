# Wallpapers

A personal collection of wallpapers, plus a small CLI to set them as your background via [swaybg](https://github.com/swaywm/swaybg).

## Gallery

Browse the full collection with thumbnails: **[GALLERY.md](GALLERY.md)**

The gallery is regenerated automatically whenever images under `walls/` change (see [`.github/workflows/gallery.yml`](.github/workflows/gallery.yml)).

## Usage

```
./wallpaper [-m mode] [-r <dir>] [-t <seconds>] [<image>]
  -m mode      stretch|fill|fit|center|tile|solid_color (default: fill)
  -r <dir>     rotate through random images from directory (recursive)
  -t <seconds> rotation interval (default: 60; <= 0 disables rotation, sets once)
  <image>      path to image file
```

With `-r`, a random image is set immediately, then a background loop swaps in a new
random image from that directory every `-t` seconds (default 60) until you run
`./wallpaper` again. Pass `-t 0` (or any value `<= 0`) to just set one random image
without starting the rotation loop.

Examples:

```
./wallpaper -r walls              # random wallpaper, rotating every 60s
./wallpaper -r walls -t 300       # rotate every 5 minutes
./wallpaper -r walls -t 0         # single random wallpaper, no rotation
./wallpaper -m fit some.jpg       # set a specific image with a given mode
```
