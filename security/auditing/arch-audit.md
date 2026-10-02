# arch-audit

`arch-audit` lists known vulnerabilities in the packages installed on this machine. The data comes from the Arch Linux security tracker.

```bash
$ sudo pacman -S arch-audit
$ arch-audit
$ arch-audit -u
```

The first command prints every affected package. `-u` prints only the ones that already have a fixed package in the repos. Those are cleared by upgrading:

```bash
$ sudo pacman -Syu
```

A package with no `-u` line has no fixed build yet. Removing it, or waiting, are the two options. `arch-audit` does not scan file contents. It compares installed versions with the tracker.
