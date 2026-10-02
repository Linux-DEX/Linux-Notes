# fwupd

fwupd updates device firmware from the Linux Vendor Firmware Service. The daemon starts on demand. You do not enable a service by hand.

```bash
$ sudo pacman -S fwupd
$ fwupdmgr get-devices
$ fwupdmgr refresh
$ fwupdmgr get-updates
$ fwupdmgr update
```

`get-devices` lists hardware fwupd can see. `refresh` downloads the current firmware catalog. It needs a network. `get-updates` lists updates for the devices you have and does not install them. `update` downloads and applies those updates.

Stay on AC power while `update` runs. Do not power off if it asks for a reboot. Some devices only finish the update on the next boot.
