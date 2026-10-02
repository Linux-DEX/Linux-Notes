# iftop

iftop shows which connections on this machine are using bandwidth. nethogs, in `security/network/nethogs.md`, groups the same traffic by process.

```bash
$ sudo pacman -S iftop
$ sudo iftop -i <interface>
$ sudo iftop -i <interface> -nP
```

Each row is a pair of addresses and the rate between them. `-n` skips DNS lookups. `-P` adds the port. Quit with `q`. It only listens. It does not change the interface.
