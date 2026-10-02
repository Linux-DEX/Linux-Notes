# cron

cron runs a command on a clock. systemd timers are in `linux/systemd.md`. Use cron when the job is a shell command and not already a service.

```bash
$ sudo pacman -S cronie
$ sudo systemctl enable --now cronie
$ crontab -e
$ crontab -l
```

`crontab -e` edits your user's table. `crontab -l` prints it. Each line is five fields and then the command:

```text
minute hour day-of-month month day-of-week command
```

A star means every value of that field. cron's `PATH` is short, so the command should be an absolute path.

```text
0 9 * * * /usr/bin/date >> /home/<user>/cron.log
```

That line appends the date to the log at 09:00 every day. `crontab -r` deletes the whole table for your user.
