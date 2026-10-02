# mkinitcpio

The initramfs is the small image the bootloader loads before the real root filesystem is mounted. It contains the modules needed to find that disk. On Arch, `mkinitcpio` builds it.

Installing or upgrading a kernel package runs `mkinitcpio` for you, through a pacman hook. `pacman -S linux-lts` already produces `/boot/initramfs-linux-lts.img`. Run it by hand when you change the initramfs config, not after a normal kernel install.

## Presets

One preset per installed kernel, in `/etc/mkinitcpio.d/`.

| Package | Preset | Image |
| ------- | ------ | ----- |
| `linux` | `linux.preset` | `/boot/initramfs-linux.img` |
| `linux-lts` | `linux-lts.preset` | `/boot/initramfs-linux-lts.img` |
| `linux-zen` | `linux-zen.preset` | `/boot/initramfs-linux-zen.img` |
| `linux-hardened` | `linux-hardened.preset` | `/boot/initramfs-linux-hardened.img` |

Each preset also builds a `-fallback` image. The fallback image skips autodetection and includes more modules. Boot that entry when the default image cannot see the disk.

## Rebuild

```bash
$ sudo mkinitcpio -P
$ sudo mkinitcpio -p linux
```

`-P` rebuilds every preset. `-p` rebuilds one.

The config is `/etc/mkinitcpio.conf`. The line that matters is `HOOKS`. After you edit it, run `mkinitcpio -P` before you reboot.

A root filesystem on LUKS needs the `encrypt` hook (or `sd-encrypt`) before the `filesystems` hook, plus a kernel parameter the bootloader passes. A data disk that is not root does not. That case is `/etc/crypttab`, in `linux/luks.md`.

The boot menu has to name the new image. Regenerating GRUB is in `linux/kernel-and-boot.md`.
