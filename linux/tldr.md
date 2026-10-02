# tldr

tldr prints a short example page for a command. The pages are a cache on disk. The Arch package is `tealdeer`. The command is `tldr`.

```bash
$ sudo pacman -S tealdeer
$ tldr --update
$ tldr tar
$ tldr --list
```

`--update` downloads the pages. The first lookup needs that cache. `--list` prints every page in the cache. `tldr <command>` prints the examples for that command.
