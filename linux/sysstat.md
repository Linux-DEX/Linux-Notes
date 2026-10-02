# sysstat

sysstat reports CPU and disk activity on this machine. iotop, in `linux/iotop.md`, is the per-process disk view. These commands are per CPU and per disk device.

```bash
$ sudo pacman -S sysstat
$ mpstat -P ALL 1
$ iostat -xz 1
$ pidstat 1
```

The `1` is the interval in seconds. `mpstat` is one line per CPU. `iostat -x` adds service time and utilization. `-z` hides disks that were idle. `pidstat` is CPU per process. Ctrl-C stops them. The first sample is the average since boot. Later lines are that one-second window.
