# Firewall

Arch boots with no packet filter loaded. The kernel firewall is nftables.

## What is loaded

```bash
$ sudo nft list ruleset
```

Empty output means nothing is filtering. `iptables -L` on current Arch is a frontend to the same nftables rules (`iptables-nft`), not the old iptables kernel backend.

## A frontend, if you do not want to write rules

`ufw` and `firewalld` both generate nftables rules. Install one of them. Running both means two tools rewrite one ruleset.

```bash
$ sudo pacman -S ufw
$ sudo ufw status
```

`ufw` stays off until you enable it. If you are connected over SSH, allow that port before you enable it. `ufw enable` with the default incoming policy will drop the session you are using.

```bash
$ sudo ufw allow 22/tcp
$ sudo ufw enable
$ sudo ufw status verbose
```

`22/tcp` is the OpenSSH default. If `sshd` listens on another port, allow that port instead. Check with `ss -tlnp`.
