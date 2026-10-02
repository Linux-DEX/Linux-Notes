# foremost

foremost carves files out of a disk image by header and footer. PhotoRec, in `security/forensics/testdisk.md`, is the other carver. foremost is the one Kali lists beside it, and it is not interactive.

```bash
$ sudo pacman -S foremost
$ foremost -i disk.img -o /other/disk/recovered
$ foremost -t jpg,pdf -i disk.img -o /other/disk/recovered
```

`-i` is the image to read. `-o` is the directory that receives the files. That directory must be on a different disk from the one the image came from. `-t` limits the types. With no `-t`, foremost uses `/etc/foremost.conf`.

It creates one subdirectory per type (`jpg/`, `pdf/`) inside `-o`. Names are numbered. It does not restore original paths.
