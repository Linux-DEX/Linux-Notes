# USBGuard

USBGuard blocks USB devices that are not in its policy. Generate that policy while every device you need is already plugged in, including the keyboard if it is USB. A policy built without the keyboard will block the keyboard the next time it reconnects.

```bash
$ sudo pacman -S usbguard
$ sudo usbguard generate-policy | sudo tee /etc/usbguard/rules.conf >/dev/null
$ sudo chmod 600 /etc/usbguard/rules.conf
$ usbguard list-devices
```

Read the list before you start the daemon. The keyboard and mouse you are using should be in it.

```bash
$ sudo systemctl enable --now usbguard
```

A device plugged in later is blocked until you allow that id. `permanent` writes the allow into the policy so it survives a restart.

```bash
$ usbguard list-devices
$ sudo usbguard allow-device <id> permanent
```
