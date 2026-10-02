# tmux

tmux keeps a terminal session running after you disconnect. The prefix key is Ctrl-b. Release it, then press the command key.

```bash
$ sudo pacman -S tmux
$ tmux new -s work
```

Detach with Ctrl-b then d. The session keeps running.

```bash
$ tmux ls
$ tmux attach -t work
$ tmux kill-session -t work
```

Inside a session:

| Keys | Effect |
| ---- | ------ |
| Ctrl-b c | New window |
| Ctrl-b n | Next window |
| Ctrl-b p | Previous window |
| Ctrl-b % | Split side by side |
| Ctrl-b " | Split top and bottom |
| Ctrl-b arrows | Move to the pane in that direction |
| Ctrl-b d | Detach |
