# Sleuth Kit

Sleuth Kit reads a disk image without mounting it. The image is a file you already have, from a disk you are allowed to examine. It does not take the image. `dd` in `linux/commands.md` is one way an image gets made.

```bash
$ sudo pacman -S sleuthkit
$ mmls disk.img
```

`mmls` prints the partition table. The `Start` column is the sector offset of that filesystem. Later commands need that number as `-o`.

```bash
$ fsstat -o <start> disk.img
$ fls -o <start> disk.img
$ fls -r -o <start> disk.img
```

`fsstat` is the filesystem type, size, and block size. `fls` lists the root directory. `-r` walks subdirectories. The number at the start of a line is the inode.

```bash
$ icat -o <start> disk.img <inode> > recovered.bin
```

`icat` writes that inode's bytes to stdout. Redirect it to a file on a different disk from the one the image came from.
