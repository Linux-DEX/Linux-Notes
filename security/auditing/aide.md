# AIDE

AIDE records hashes and metadata for files, then reports what changed. It does not decide whether a change was legitimate. You do, when you read the report.

```bash
$ sudo pacman -S aide
$ sudo aide --init
$ sudo mv /var/lib/aide/aide.db.new.gz /var/lib/aide/aide.db.gz
```

`--init` writes the baseline to `aide.db.new.gz`. Checks read `aide.db.gz`, so the move is the step that makes the baseline the one in use. The paths come from `/etc/aide.conf`.

```bash
$ sudo aide --check
```

After a change you meant to make, rebuild the baseline. `--update` writes a new `aide.db.new.gz` and still leaves the old baseline in place until you move the new file over it.

```bash
$ sudo aide --update
$ sudo mv /var/lib/aide/aide.db.new.gz /var/lib/aide/aide.db.gz
```
