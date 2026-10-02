# checksec

checksec reports the exploit mitigations compiled into a binary or running process: stack canary, NX, PIE, RELRO, and Fortify.

```bash
$ sudo pacman -S checksec
$ checksec --file=/usr/bin/ls
$ checksec --dir=/usr/bin
$ checksec --proc-all
```

`--file` is one binary. `--dir` is every ELF in that directory. `--proc-all` is every process you are allowed to read. Run it with sudo if you want processes owned by other users.

A missing mitigation is a property of how that program was built. checksec does not change the binary. The fix is a rebuild with the hardening flags, or a newer package.
