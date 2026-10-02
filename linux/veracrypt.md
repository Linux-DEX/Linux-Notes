# VeraCrypt

VeraCrypt stores files in an encrypted container. LUKS, in `linux/luks.md`, encrypts a whole disk. A container is one file you can copy.

```bash
$ sudo pacman -S veracrypt
$ veracrypt -t -c
$ sudo mkdir -p /mnt/vc
$ sudo veracrypt -t <container> /mnt/vc
$ sudo veracrypt -t -d
```

`-c` asks for the file path, the size, and a password, then writes the container. The mount command asks for that password and attaches the filesystem at `/mnt/vc`. `-d` detaches it. Without the password the file stays unreadable.
