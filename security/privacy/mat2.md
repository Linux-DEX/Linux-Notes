# mat2

`mat2` removes metadata from a copy of a file: author names, GPS coordinates, and the application that wrote it. The original file is left in place.

```bash
$ sudo pacman -S mat2
$ mat2 --show <file>
$ mat2 <file>
```

`--show` prints the metadata and changes nothing. `mat2` writes `<file>.cleaned.<ext>` beside the original. Open the cleaned file and check it. `--inplace` overwrites the original, so the uncleaned copy is gone.
