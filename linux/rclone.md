# rclone

rclone copies files to a storage account you control. restic, in `linux/backups.md`, is the encrypted snapshot tool. rclone is the copy to a remote.

```bash
$ sudo pacman -S rclone
$ rclone config
$ rclone lsd <remote>:
$ rclone copy <local-dir> <remote>:<path>
```

`config` asks for the remote name and credentials and writes them to `~/.config/rclone/rclone.conf`. That file is a secret. `lsd` lists directories on the remote. `copy` adds and updates files. It does not delete files that exist only on the remote.

`rclone sync` does delete those. Use it only when the remote should become an exact copy of the local directory.
