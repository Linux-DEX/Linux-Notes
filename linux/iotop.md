# iotop

iotop shows which process is reading and writing disk, the same way `top` shows CPU.

```bash
$ sudo pacman -S iotop
$ sudo iotop
$ sudo iotop -o
```

`-o` hides processes that are not doing I/O. Quit with `q`. The left columns are current read and write rates. The total columns are bytes since iotop started.
