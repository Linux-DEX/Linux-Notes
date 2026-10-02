# Wayland keyd

- This tool is used to map the keybinding in linux for wayland, and disable the key.

```bash
yay -S keyd
```

- Create config in `/etc/keyd/default.conf`:

```bash
[ids]
*

[main]
backspace = void
delete = backspace
```

- Enable and start the keyd daemon

```bash
sudo systemctl enable keyd
sudo systemctl start keyd
```

- Restart the service:
```bash
sudo systemctl restart keyd
```
