# Wallpapers

A personal collection of wallpapers, plus a small CLI to set them as your background via [swaybg](https://github.com/swaywm/swaybg).

## Gallery

Browse the full collection with thumbnails: **[GALLERY.md](GALLERY.md)**

The gallery is regenerated automatically whenever images under `walls/` change (see [`.github/workflows/gallery.yml`](.github/workflows/gallery.yml)).

## Usage

```
./wallpaper [-m mode] [-r <dir>] [<image>]
  -m mode   stretch|fill|fit|center|tile|solid_color (default: fill)
  -r <dir>  pick random image from directory (recursive)
  <image>   path to image file
```

Examples:

```
./wallpaper -r walls           # random wallpaper from the whole collection
./wallpaper -m fit some.jpg    # set a specific image with a given mode
```
