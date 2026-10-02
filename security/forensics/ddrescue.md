# ddrescue

GNU ddrescue copies a disk you own onto an image file, and it keeps going when sectors fail. The image is what Sleuth Kit, foremost, and PhotoRec read later. The copy has to land on a different disk. Unmount the disk you are reading before you start.

```bash
$ sudo pacman -S ddrescue
$ sudo ddrescue -f -n /dev/<disk> /other/disk/disk.img /other/disk/disk.map
$ sudo ddrescue -d -f -r3 /dev/<disk> /other/disk/disk.img /other/disk/disk.map
```

The first path is the disk. The second is the image. The third is the map file, which records which sectors are done. `-n` is a first pass that skips the slow retries. Run the second command with the same three paths to retry the bad spots. `-f` is required once `disk.img` already exists, which is every resume. `-r3` tries each remaining sector three times.

`ddrescuelog` reads the map file. It does not copy the disk.

```bash
$ ddrescuelog -t /other/disk/disk.map
```
