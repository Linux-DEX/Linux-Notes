# ethtool

ethtool reads the link state of a network interface on this machine: speed, duplex, and which driver is bound.

```bash
$ sudo pacman -S ethtool
$ sudo ethtool <interface>
$ sudo ethtool -i <interface>
$ sudo ethtool -S <interface>
```

The first command is whether the link is up and at what speed. `-i` is the driver and firmware version. `-S` is the driver's counters. These commands do not change the interface.
