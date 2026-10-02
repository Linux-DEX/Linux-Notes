# mtr

mtr combines ping and traceroute. It keeps sending probes and updates a table of hops.

```bash
$ sudo pacman -S mtr
$ mtr <host>
```

Quit with `q`. A single report, ten rounds, numeric addresses:

```bash
$ mtr -n -r -c 10 <host>
```

`-n` skips DNS lookups. `-r` prints the report and exits. `-c` is how many probes to send. Loss or rising latency on one hop is that hop. Loss that starts at one hop and continues through every hop after it is that hop or the link past it.
