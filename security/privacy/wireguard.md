# WireGuard

WireGuard is a VPN. `wireguard-tools` supplies `wg` and `wg-quick`. These notes are the commands. The peer at the other end is a machine you run, or a provider you already have an account with.

```bash
$ sudo pacman -S wireguard-tools
$ umask 077
$ wg genkey | tee privatekey | wg pubkey > publickey
```

`umask 077` makes `privatekey` readable only by you. The public key is what you give the other peer. The private key stays in the config on this machine and does not go in this notes repo.

A tunnel file is `/etc/wireguard/<name>.conf`:

```text
[Interface]
PrivateKey = <private key>
Address = <address>/<prefix>

[Peer]
PublicKey = <peer public key>
Endpoint = <host>:<port>
AllowedIPs = <cidr>
```

`AllowedIPs` is the set of addresses that go through the tunnel. `0.0.0.0/0` sends all IPv4 traffic into it.

```bash
$ sudo wg-quick up <name>
$ wg show
$ sudo wg-quick down <name>
```

`<name>` is the file name without `.conf`. To bring that same file up on boot:

```bash
$ sudo systemctl enable --now wg-quick@<name>
```
