# ShellCheck

ShellCheck reads a shell script and prints the bugs and quoting problems it can see without running the script.

```bash
$ sudo pacman -S shellcheck
$ shellcheck script.sh
$ shellcheck -x script.sh
```

Each finding has a code such as `SC2086`. The line and the message say what to change. `-x` follows files the script sources, so those files are checked too.

ShellCheck does not run the script and does not edit it. A clean run prints nothing and exits 0.
