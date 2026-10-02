# inotify-tools

inotifywait prints filesystem events as they happen in a directory you choose. It is a live watch, not a record of the past.

```bash
$ sudo pacman -S inotify-tools
$ inotifywait -m -r -e modify,create,delete <directory>
```

`-m` keeps running. `-r` includes subdirectories that already exist. Each line is the directory, the event, and the filename. Ctrl-C stops it. It does not block the change.
