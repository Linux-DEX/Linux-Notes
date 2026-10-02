# arpwatch

arpwatch watches one Ethernet interface and records which MAC address owns each IP. A MAC that changes for an IP that was already seen is called a flip-flop. On a quiet LAN that is the usual sign of ARP spoofing.

```bash
$ sudo pacman -S arpwatch
$ ip -br link
$ sudo systemctl enable --now arpwatch@<interface>
$ journalctl -u arpwatch@<interface> -f
```

`<interface>` is the name from `ip -br link`, such as `enp0s31f6`. The `@` unit is one instance per interface.

The database is `/var/lib/arpwatch/arp.dat`. A "new station" line is a MAC this interface had not seen. A "flip flop" line is an IP that moved to a different MAC. arpwatch also tries to mail root. The journal has the same lines either way.

```bash
$ sudo systemctl stop arpwatch@<interface>
$ sudo systemctl disable arpwatch@<interface>
```
