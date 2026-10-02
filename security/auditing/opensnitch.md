# OpenSnitch

OpenSnitch is an application firewall. It asks, in a desktop window, when a program opens a connection.

```bash
$ sudo pacman -S opensnitch
$ sudo systemctl enable --now opensnitchd
$ opensnitch-ui
```

`opensnitchd` is the daemon. `opensnitch-ui` is the window that shows the prompt. Decisions you make there are stored as rules.

If the UI is not running, the daemon uses the default action in `/etc/opensnitchd/default-config.json`. That default is allow, so a closed UI does not cut the machine off the network. Prompts only appear while `opensnitch-ui` is open.
