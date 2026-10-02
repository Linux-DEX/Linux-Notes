# LUKS

LUKS is disk encryption handled by `cryptsetup`. The passphrase unlocks a device in `/dev/mapper/`. You mount that mapper device, not the raw partition.

This page is a data disk, such as the backup drive. Encrypting the root filesystem is a different setup: an initramfs hook, documented in `linux/mkinitcpio.md`.

## See if a partition is encrypted

```bash
$ lsblk -f
```

The type column says `crypto_LUKS` for an encrypted partition.

## Open and close

```bash
$ sudo cryptsetup open /dev/sdb1 backup
$ sudo mount /dev/mapper/backup /media/Backup
$ sudo umount /media/Backup
$ sudo cryptsetup close backup
```

`backup` is the name you pick. It becomes `/dev/mapper/backup`. Unmount before `close`. `cryptsetup status backup` shows whether it is open.

## Open it at boot

`/etc/crypttab` is read before `/etc/fstab`. `none` in the third field means ask for the passphrase.

```text
backup  UUID=<uuid>  none  luks,nofail
```

The UUID is the LUKS container, from `lsblk -f` on `/dev/sdb1`, not the filesystem inside it.

Then fstab mounts the mapper, not `/dev/sdb1`:

```text
/dev/mapper/backup  /media/Backup  ext4  defaults,nofail  0  2
```

`nofail` on both lines lets boot continue when the disk is unplugged. Without it, a missing backup disk drops you into the emergency shell in `linux/troubleshooting.md`.
