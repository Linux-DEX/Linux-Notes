# Volatility 3

Volatility reads a memory dump you already have from a machine you administer. It lists what was running. It does not take the dump.

```bash
$ sudo pacman -S volatility3
$ vol -f memory.raw windows.info
$ vol -f memory.raw linux.pslist
```

`-f` is the dump. `windows.info` prints the Windows version in that dump. `linux.pslist` prints the process list from a Linux dump. The plugin prefix has to match the OS that produced the file. A mismatch, or a dump Volatility has no symbols for, prints an error and stops. `vol -h` lists the plugins. Volatility does not change the dump.
