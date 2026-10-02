# Pacman mirrors

Pacman downloads from the servers in `/etc/pacman.d/mirrorlist`, top one first. A dead or distant mirror makes `-Syu` look like a failed upgrade.

`reflector` rewrites that file from the current mirror status.

```bash
$ sudo pacman -S reflector
$ sudo cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak
$ sudo reflector --country India --protocol https --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```

`--latest 10` keeps the ten most recently synced mirrors in that country. `--sort rate` puts the fastest first. `--save` replaces the mirrorlist. The `.bak` copy is how you put the old list back.

Refresh the package database after the list changes:

```bash
$ sudo pacman -Sy
```

## On a timer

The package ships `reflector.timer`. It reads `/etc/xdg/reflector/reflector.conf`, which is a list of the same options.

```bash
$ systemctl enable --now reflector.timer
$ systemctl list-timers reflector.timer
```
