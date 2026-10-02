# tcpdump

`tcpdump` prints packet headers on an interface of this machine. Use it to see who this host is talking to. `ss` in `linux/commands.md` is the better view of sockets that are already open.

```bash
$ sudo pacman -S tcpdump
$ sudo tcpdump -n -c 20 -i any
```

`-n` does not look up hostnames. `-c 20` stops after 20 packets. `-i any` is every interface on this machine.

Limit it to one port:

```bash
$ sudo tcpdump -n -c 20 -i any tcp port 443
$ sudo tcpdump -n -c 20 -i any udp port 53
```

The first is HTTPS connections. The second is DNS. Both print headers, not a saved capture of the traffic.
