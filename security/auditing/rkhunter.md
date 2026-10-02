# rkhunter

rkhunter compares the system with a list of known rootkit files and with a baseline of file properties.

```bash
$ sudo pacman -S rkhunter
$ sudo rkhunter --update
$ sudo rkhunter --propupd
$ sudo rkhunter --check --sk
```

`--update` refreshes the signature files. `--propupd` records hashes and permissions of the current system. Run that only when you trust the machine, such as just after install and again after you have read a clean check. A baseline taken on a compromised system makes the compromise look normal.

`--check` is the scan. `--sk` does not wait for a keypress between tests. The report is `/var/log/rkhunter.log`.

A warning on Arch is often a false positive. Read the log line before treating it as a rootkit. `unhide`, in `security/auditing/unhide.md`, is the process check rkhunter can call.
