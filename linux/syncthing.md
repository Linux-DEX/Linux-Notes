# Syncthing

Syncthing keeps a folder the same on two machines you control. The web UI listens on this machine only.

```bash
$ sudo pacman -S syncthing
$ systemctl --user enable --now syncthing
```

Open `http://127.0.0.1:8384`. The Actions menu shows this device's ID. On the other machine, add that ID as a remote device, then share a folder with it. The other side has to accept the folder.

```bash
$ systemctl --user status syncthing
$ systemctl --user stop syncthing
```

The user service runs while you are logged in, and after logout if lingering is on for that user (`loginctl enable-linger`). Do not publish port 8384 past localhost. The GUI is an admin page for the sync, not a file share.
