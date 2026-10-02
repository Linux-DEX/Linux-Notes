# BleachBit

BleachBit deletes caches, temporary files, and some application history. Preview before you clean. A cleaner can remove more than you expect, including saved site data.

```bash
$ sudo pacman -S bleachbit
$ bleachbit
$ bleachbit --list-cleaners
```

The window is the picker. On the command line, `--list-cleaners` prints names such as `system.tmp`.

```bash
$ bleachbit --preview system.tmp
$ bleachbit --clean system.tmp
```

`--preview` lists what would be deleted and deletes nothing. `--clean` deletes that cleaner. Run a cleaner you have read. Do not pass every name from the list in one command.

Some cleaners need root because the files are outside your home directory:

```bash
$ sudo bleachbit --preview system.tmp
$ sudo bleachbit --clean system.tmp
```
