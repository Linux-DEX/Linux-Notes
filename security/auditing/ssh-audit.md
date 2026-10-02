# ssh-audit

`ssh-audit` connects to an SSH server and grades the algorithms and options in the banner. Run it against a server you administer. The matching server settings are in `linux/services.md`.

```bash
$ sudo pacman -S ssh-audit
$ ssh-audit localhost
```

A red or failing line is an algorithm or option the tool considers weak. Change `/etc/ssh/sshd_config`, check it, reload, and run `ssh-audit` again.

```bash
$ sudo sshd -t
$ sudo systemctl reload sshd
$ ssh-audit localhost
```

If `sshd` is not listening on port 22:

```bash
$ ssh-audit -p <port> localhost
```
