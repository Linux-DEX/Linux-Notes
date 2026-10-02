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

