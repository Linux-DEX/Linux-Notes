# unhide

unhide looks for processes that are hidden from the normal process list. That is a rootkit symptom. A hit is a pid you should be able to explain.

```bash
$ sudo pacman -S unhide
$ sudo unhide quick
$ sudo unhide proc
$ sudo unhide sys
```

`quick` is the short combined test. `proc` compares `/proc` with the process table. `sys` uses system calls. Hidden ports, rather than hidden processes:

```bash
$ sudo unhide-tcp
```

Nothing printed means these tests did not find a hidden process. A pid in the output is one that `ps` did not show. Confirm it before deleting anything. The test can false-positive on short-lived processes.
