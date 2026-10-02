# auditd

The audit daemon records security events the kernel was asked to log. Login records are the useful default. This is not a keystroke log.

```bash
$ sudo pacman -S audit
$ sudo systemctl enable --now auditd
$ sudo ausearch -m USER_LOGIN -ts today
$ sudo aureport --auth
```

`ausearch` prints the matching events. `aureport --auth` is the short count of authentication successes and failures. `auditctl -l` prints the active rules.

Adding a rule that records every program execution fills the disk. Keep the ruleset to the events you will actually read.
