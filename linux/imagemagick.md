# ImageMagick

ImageMagick reads and writes images. On current Arch the command is `magick`.

```bash
$ sudo pacman -S imagemagick
$ magick identify photo.jpg
$ magick photo.jpg -resize 50% photo-small.jpg
$ magick photo.jpg photo.png
$ magick *.jpg images.pdf
```

`identify` prints format, dimensions, and color depth. It does not write a file. `-resize 50%` is half the width and half the height. Changing the extension converts the format. The last argument is the file that gets written. A name that already exists is overwritten.

Several inputs and one `.pdf` output puts those images into one PDF, in the order the shell expands the names.
