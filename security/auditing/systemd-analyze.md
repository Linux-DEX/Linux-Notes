# systemd-analyze security

`systemd-analyze security` scores how loosely a service is sandboxed. A high number means the unit is allowed to do more. It is not a list of known vulnerabilities.

```bash
$ systemd-analyze security
$ systemd-analyze security sshd
```

The first command prints every service. The second explains one unit: which sandbox options are on, and which are off. Turning an option on is a change to that unit's drop-in, covered in `linux/systemd.md`.
