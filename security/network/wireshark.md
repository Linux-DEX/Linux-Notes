# Wireshark

Wireshark is the graphical view of the same kind of capture as `tcpdump`. Capture on an interface of this machine.

```bash
$ sudo pacman -S wireshark-qt
$ sudo usermod -aG wireshark "$USER"
```

Group membership applies to the next login. After that, Wireshark captures through `dumpcap` without running the whole GUI as root.

Pick the interface, start the capture, stop it. A display filter keeps the packet list to one port:

```text
tcp.port == 443
```

The packet list is headers and a protocol tree. Saving a capture writes a pcap next to whatever you were looking at. Don't leave those files around if the traffic was not yours to keep.
