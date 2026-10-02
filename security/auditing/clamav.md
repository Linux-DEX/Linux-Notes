# ClamAV

ClamAV scans files for known malware signatures. Signatures do not catch a new sample that is not in the database yet.

```bash
$ sudo pacman -S clamav
$ sudo freshclam
```

`freshclam` downloads the database into `/var/lib/clamav`. A scan before that finishes reports that the database is missing. The `clamav-freshclam` service repeats the download.

```bash
$ sudo systemctl enable --now clamav-freshclam.service
```

## Scan

```bash
$ clamscan --recursive --infected /home
```

`--infected` prints only hits. `--recursive` walks directories. Scan a tree you choose. A hit names the file and the signature. Quarantine is moving that file out of the way yourself. `clamscan` does not delete it unless you pass `--remove`, and a false positive would then be gone.
