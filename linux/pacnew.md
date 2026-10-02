# .pacnew files

`pacman -Syu` does not overwrite a config file you have edited. It leaves the package's new copy beside yours and prints a warning.

| File | When pacman creates it |
| ---- | ---------------------- |
| `file.pacnew` | Upgrade. You changed a file the package marks as a config. Your file stays. The new one is `file.pacnew`. |
| `file.pacsave` | Removal. You had changed that config, so pacman renames yours to `file.pacsave` instead of deleting it. |
| `file.pacorig` | Install. A file was already there and no package owned it. Pacman renames the old one to `file.pacorig` and writes the package file. |

## See them

`pacdiff` is in `pacman-contrib`, not in `pacman`.

```bash
$ sudo pacman -S pacman-contrib
$ sudo pacdiff -o
```

`-o` only lists the files. Drop `-o` to open each pair. `nvim -d` is diff mode, which is what `vimdiff` does.

```bash
$ sudo DIFFPROG="nvim -d" pacdiff
```

## Merge

For each pair, the file without the suffix is the one the system is using. Copy across the settings you still need from the `.pacnew`, then delete the `.pacnew`.

```bash
$ sudo rm /etc/ssh/sshd_config.pacnew
```

Deleting a `.pacnew` without reading it keeps your old config and drops whatever the new package changed. That is the right call only when you have looked at the diff.
