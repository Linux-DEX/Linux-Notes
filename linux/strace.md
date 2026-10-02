# strace

strace prints the system calls a process makes. Run it on a command you start, or on a process you own.

```bash
$ sudo pacman -S strace
$ strace <command>
$ strace -o trace.txt <command>
$ strace -c <command>
$ strace -e openat,connect <command>
$ strace -p <pid>
```

`-o` writes the trace to a file instead of the terminal. `-c` prints a count and the time per system call, not every call. `-e` limits the trace to those calls. `openat` is files the process opens. `connect` is outgoing connections.

`-p` attaches to a running pid. Detach with Ctrl-c. That stops the trace and leaves the process running. Attaching can slow the process a lot.
