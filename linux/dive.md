# dive

dive shows the layers inside a container image that is already on this machine. Building and running images is `linux/docker.md`.

```bash
$ sudo pacman -S dive
$ dive <image>
```

The left pane is each layer. The right pane is the files that layer added, changed, or removed. Quit with `q` or Ctrl-C. dive does not push, delete, or run the image.
