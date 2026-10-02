# NETWORK MANAGER (to connect to wifi)

## Connect to wifi
```bash
$ nmcli dev wifi connect "<ssid>" password "<password>"
```

## Delete the network
```bash
$ nmcli con delete "<ssid>"
```

## Disconnect
```bash
$ nmcli con down <wifi-name>
```

## Check wifi connection
```bash
$ nmcli con
```

## Check available wifi
```bash
$ nmcli d wifi list
```

## Turn on wifi
```bash
$ nmcli r wifi on
```

## Turn off wifi
```bash
$ nmcli r wifi off
```

## Show password
```bash
$ nmcli device wifi show-password
```

# Address and DNS

`nmcli con` prints the connection name. The commands below use that name, which is often the SSID.

## What you have now

```bash
$ ip route
$ nmcli -f IP4 con show "<name>"
$ cat /etc/resolv.conf
```

`ip route` shows the default gateway. The `IP4.DNS` line is what NetworkManager was given. `/etc/resolv.conf` is what processes actually read. On Arch, NetworkManager writes that file unless `systemd-resolved` is enabled.

## Static address

```bash
$ nmcli con mod "<name>" ipv4.method manual \
    ipv4.addresses <address>/<prefix> \
    ipv4.gateway <gateway> \
    ipv4.dns "<dns>"
$ nmcli con up "<name>"
```

`ipv4.method manual` stops DHCP. `<prefix>` is the mask length, `24` for `255.255.255.0`. Bring the connection up or the change sits in the file unused.

DHCP again:

```bash
$ nmcli con mod "<name>" ipv4.method auto
$ nmcli con mod "<name>" ipv4.addresses "" ipv4.gateway ""
$ nmcli con up "<name>"
```

## DNS only

Keep DHCP addresses, replace the DNS servers:

```bash
$ nmcli con mod "<name>" ipv4.ignore-auto-dns yes ipv4.dns "<dns>"
$ nmcli con up "<name>"
```

`ipv4.ignore-auto-dns yes` drops the DNS servers from DHCP. Without it, NetworkManager merges them with yours.

# BLUETOOTH MANAGER
## Check bluetooth status
```bash
$ sudo systemctl status bluetooth
```

## Enable service
```bash
$ sudo systemctl enable bluetooth
```

## Start bluetooth
```bash
$ sudo systemctl start bluetooth
```

## Scan
```bash
$ bluetoothctl scan on
```

## Discoverable to other devices
```bash
$ bluetoothctl discoverable on 
```

## Pair device
```bash
$ bluetoothctl pair <device-id>
```

## Connect device
```bash
$ bluetoothctl connect <device-id>
```

## List pair device
```bash
$ bluetoothctl paired-devices
```

## List devices within bluetooth range
```bash
$ bluetooth devices

$ bluetoothctl <option> <device-id>
```

## option
### trust
### remove
### block
### untrust
### disconnect

