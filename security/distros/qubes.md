# Qubes OS

Qubes is a separate operating system, not an Arch package. Each application group runs in its own virtual machine, called a qube. A template qube holds the root filesystem. An app qube is what you start and use. BlackArch, in `security/distros/blackarch.md`, is the other kind of security distro in these notes: a pentest package set on top of Arch. Qubes is for separating work, not for collecting attack tools.

These commands exist only when you are booted into Qubes.

```bash
$ qvm-ls
$ qvm-start <qube>
$ qvm-run <qube> <command>
$ qvm-shutdown <qube>
```

`qvm-ls` shows qubes and whether they are running. `qvm-start` boots one. `qvm-run` runs one command inside it. `qvm-shutdown` powers that qube off. The window manager starts an app qube for you when you pick an application from its menu. That is the same start, without typing `qvm-start`.
