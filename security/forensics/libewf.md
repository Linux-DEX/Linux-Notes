# libewf

libewf writes and checks an Expert Witness (`.E01`) disk image. The image stores a checksum for each block, so you can tell later if the file changed. The source is a disk you are allowed to image. Write the `.E01` to a different disk, and unmount the source first.

```bash
$ sudo pacman -S libewf
$ sudo ewfacquire -t /other/disk/case /dev/<disk>
$ ewfinfo /other/disk/case.E01
$ ewfverify /other/disk/case.E01
```

`-t` is the image path without the extension. `ewfacquire` asks for case text, then writes `case.E01`. `ewfinfo` prints the size and that text. `ewfverify` recomputes the block checksums.

Sleuth Kit is built against this library, so the same image works there:

```bash
$ mmls /other/disk/case.E01
```
