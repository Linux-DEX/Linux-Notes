# firejail

`firejail` runs a program with a mount, network, and user namespace restricted by a profile. Profiles ship in `/etc/firejail/`.

```bash
$ sudo pacman -S firejail
$ firejail firefox
$ firejail --list
```

`firefox` with no extra flags uses the Firefox profile and your normal home directory, with the profile's denials applied. `--list` shows jails running as you.

Tor Browser should be started as itself, not inside `firejail`. The Tor Browser profile and a second sandbox fight over the same ports and files. See `security/privacy/tor.md`.
