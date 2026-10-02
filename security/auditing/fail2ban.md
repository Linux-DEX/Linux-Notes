# fail2ban

`fail2ban` reads the journal for repeated failed logins and bans that address in the firewall for a while. This page is the SSH jail. The server config it protects is in `linux/services.md`.

```bash
$ sudo pacman -S fail2ban
```

Do not edit `/etc/fail2ban/jail.conf`. Package upgrades replace it. A file under `jail.d` is the local jail.

`/etc/fail2ban/jail.d/sshd.local`:

```text
[sshd]
enabled = true
backend = systemd
```

`backend = systemd` is required on Arch. The stock sshd jail reads a log file this system does not keep. The journal is where `sshd` records failures.

If `ufw` is enabled, add `banaction = ufw` to that same section so fail2ban uses the firewall from `linux/firewall.md` instead of a second ruleset.

```bash
$ sudo systemctl enable --now fail2ban
$ fail2ban-client status
$ fail2ban-client status sshd
```

`status sshd` shows who is currently banned. To remove one address:

```bash
$ sudo fail2ban-client set sshd unbanip <address>
```

Bantime, find time, and max retries stay at the defaults in `jail.conf` until you set them in `sshd.local`.
