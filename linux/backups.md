# Backups with restic

`restic` stores encrypted snapshots in a repository. The backup disk these notes mount at `/media/Backup` can hold that repository. Mount the disk first. Opening it, if it is LUKS, is `linux/luks.md`.

```bash
$ sudo pacman -S restic
$ restic -r /media/Backup/restic init
```

`init` creates the repository and asks for a password. There is no recovery if that password is lost. The files in the repo are not readable without it.

## Take a snapshot

```bash
$ restic -r /media/Backup/restic backup /home --exclude '.cache'
```

`--exclude '.cache'` skips directories with that name. Each run adds a snapshot. It does not replace the previous one.

## List, check, restore

```bash
$ restic -r /media/Backup/restic snapshots
$ restic -r /media/Backup/restic check
$ restic -r /media/Backup/restic restore latest --target /tmp/restore
```

`restore` writes into the target directory. It does not put files back on top of `/home` unless that is the target you gave it.

## Drop old snapshots

```bash
$ restic -r /media/Backup/restic forget --keep-daily 7 --keep-weekly 4 --prune
```

`forget` marks snapshots outside that rule for deletion. `--prune` actually deletes their data. `--keep-daily 7` keeps one snapshot for each of the last seven days that have one. `--keep-weekly 4` keeps four weekly snapshots on top of that.
