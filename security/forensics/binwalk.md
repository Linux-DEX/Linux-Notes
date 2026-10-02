# binwalk

binwalk scans a file for embedded files: archives, filesystems, and firmware blobs inside one binary. Kali lists it under forensics. The file is one you are allowed to take apart.

```bash
$ sudo pacman -S binwalk
$ binwalk firmware.bin
$ binwalk --extract firmware.bin
```

With no `--extract`, binwalk only prints the offset and the type it recognized. `--extract` writes those pieces into a directory next to `firmware.bin` and prints that path. It does not modify `firmware.bin`.
