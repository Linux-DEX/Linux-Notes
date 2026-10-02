# dnscrypt-proxy

dnscrypt-proxy is a local DNS resolver. Programs ask `127.0.0.1`. The proxy asks an upstream resolver over an encrypted DNS protocol, so the query is not plain text on the network.

```bash
$ sudo pacman -S dnscrypt-proxy
$ sudo systemctl enable --now dnscrypt-proxy
$ systemctl status dnscrypt-proxy
```

The packaged config is `/etc/dnscrypt-proxy/dnscrypt-proxy.toml`. `listen_addresses` in that file is the address applications must use. The packaged value is `127.0.0.1:53`.

If the service fails immediately, another program already has that port:

```bash
$ ss -ulpn 'sport = :53'
$ journalctl -u dnscrypt-proxy -e
```

Point NetworkManager at the proxy. `<name>` is the connection from `nmcli con`, the same commands as in `linux/networking.md`.

```bash
$ nmcli con mod "<name>" ipv4.ignore-auto-dns yes ipv4.dns "127.0.0.1"
$ nmcli con up "<name>"
$ cat /etc/resolv.conf
```

`resolv.conf` should list `127.0.0.1`. A lookup then goes through the proxy:

```bash
$ dig example.com
```

`dig` comes from the `bind` package. If the command is missing, `sudo pacman -S bind`.
