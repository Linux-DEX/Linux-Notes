# TestDisk and PhotoRec

Both tools are in the `testdisk` package. They are interactive. Recovered files must be written to a different disk from the one you are reading. Writing them back onto the damaged disk overwrites the data you are trying to keep.

```bash
$ sudo pacman -S testdisk
$ sudo testdisk
$ sudo photorec
```

TestDisk looks for a lost partition table. The menu asks for the disk, the partition type, and then Analyse. A partition it offers to restore is a write to that disk. Read the line it will write before you confirm it.

PhotoRec ignores the filesystem and copies file types it recognizes. The menu asks for the disk to read and a directory to store what it finds. That directory has to be on another filesystem. PhotoRec does not put files back where they were. It dumps them into the directory you picked, under numbered names.
