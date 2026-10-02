# When something breaks

## Disk full

```bash
$ df -h
$ sudo du -xh / --max-depth=1 | sort -h
```

`df -h` shows which filesystem is full. `du` on that mount shows which top-level directory holds it. Run `du` again on that directory, one level down, until the file is obvious.

Two stores that grow without a person creating files:

```bash
$ journalctl --disk-usage
$ sudo journalctl --vacuum-size=500M
```

`--vacuum-size` deletes journal files until the journal is under that size. Package downloads sit in `/var/cache/pacman/pkg`. Cleaning that cache is `pacman -Sc`, in `linux/packages.md`.

## fstab dropped boot to an emergency shell

A bad line in `/etc/fstab` stops boot and asks for the root password. The journal names the unit that failed.

```bash
$ journalctl -xb -p err
$ mount -o remount,rw /
```

The root filesystem is often read-only at this prompt. The remount makes it writable. Comment out the line whose device matches the failed mount, save, and reboot.

```bash
$ systemctl reboot
```

`sudo mount -a` on a running system, before you reboot, is how you catch the same mistake. The fields are in `linux/filesystem.md`. `nofail` on a disk that is not always plugged in avoids this shell.

## Previous boot

```bash
$ journalctl -b -1 -p err
```

`-b -1` is the boot before this one. `-p err` is errors and worse. An empty answer means the journal is not kept across reboots. Creating `/var/log/journal` is in `linux/systemd.md`.
