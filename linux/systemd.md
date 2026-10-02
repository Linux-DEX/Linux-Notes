# systemd

systemd is PID 1. It starts units, restarts the ones that die, and stores their logs in the journal.

## Unit types

| Type | What it is |
| ---- | ---------- |
| service | A daemon or a one-shot command |
| socket | Starts a service when a connection arrives |
| timer | Starts a service on a schedule |
| mount | A filesystem mount, same facts as an fstab line |
| target | A group of units. Boot ends at a target |

## Where unit files live

| Path | Role |
| ---- | ---- |
| `/usr/lib/systemd/system` | Shipped by the package. Replaced on upgrade |
| `/etc/systemd/system` | Local unit or a full override. Wins over the package file |
| `/etc/systemd/system/<unit>.d/` | Drop-in snippets merged on top of the package unit |

```bash
$ systemctl cat sshd
$ sudo systemctl edit sshd
```

`edit` opens a drop-in and reloads systemd when you save. A change written straight into `/usr/lib/systemd/system` disappears on the next upgrade.

## Start, stop, boot

```bash
$ systemctl status sshd
$ systemctl is-active sshd
$ systemctl is-enabled sshd
$ sudo systemctl start sshd
$ sudo systemctl stop sshd
$ sudo systemctl restart sshd
$ sudo systemctl reload sshd
```

`reload` asks the process to reread its config. `restart` kills it and starts a new one. Use reload when the unit supports it and you cannot drop connections.

```bash
$ sudo systemctl enable --now sshd
$ sudo systemctl disable --now sshd
```

`enable` adds the boot link. Without `--now` it does not start the process today. `disable` removes the boot link and leaves a running process alone, unless `--now` is there too.

```bash
$ sudo systemctl mask <unit>
$ sudo systemctl unmask <unit>
```

`mask` points the unit at `/dev/null`, so nothing can start it. Use it when another unit keeps pulling a service back in.

```bash
$ systemctl list-units --type=service
$ systemctl list-unit-files --type=service --state=enabled
$ systemctl list-dependencies graphical.target
```

## Which target the machine boots to

```bash
$ systemctl get-default
$ sudo systemctl set-default multi-user.target
$ sudo systemctl set-default graphical.target
```

`multi-user.target` is text logins. `graphical.target` adds the display manager.

## Journal

`systemctl status` prints the last few log lines. The rest is `journalctl`.

```bash
$ journalctl -u sshd
$ journalctl -u sshd -b
$ journalctl -b -1
$ journalctl -f
$ journalctl -p err -b
$ journalctl --since "1 hour ago"
$ journalctl -k
```

| Flag | Meaning |
| ---- | ------- |
| `-u` | One unit |
| `-b` | This boot. `-b -1` is the previous boot |
| `-f` | Follow new lines |
| `-p err` | Priority error and worse |
| `-k` | Kernel messages, the same stream as `dmesg` |

On Arch the journal is kept in memory until `/var/log/journal` exists. Without that directory, `journalctl -b -1` is empty after a reboot.

```bash
$ sudo mkdir -p /var/log/journal
$ sudo systemctl restart systemd-journald
```

## Timers

```bash
$ systemctl list-timers
```

A timer unit starts a service. The schedule is `OnCalendar=` inside the timer. Package timers show up in that list.

Cron still works if `cronie` is installed. `crontab -e` edits your user crontab. A timer is the better fit when the job is already a service unit.

## After a unit file changes

```bash
$ sudo systemctl daemon-reload
```

`systemctl edit` runs this itself. A file you edited by hand in `/etc/systemd/system` does not take effect until you reload.
