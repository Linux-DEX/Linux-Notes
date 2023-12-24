# Introduction
+ ARP - Address Resolution Protocol
+ ARP Scan tool is a very fast ARP packet scanner that show every active IPv4 device on your subnet.
+ Since ARP is non-routable, this type of scanner only work on the local LAN.
+ ARP Scan tool show all active device even if they have firewalls.

# arp command
1. **Display ARP Cache:**
```bash
$ arp
```

2. **Display ARP Table of Specific Interface:**
```bash
$ arp -i <interface>
```

3. **Flush ARP Cache:**
```bash
$ sudo arp -d
```

4. **Flush ARP Cache for Specific Interface:**
```bash
$ sudo arp -d -i <interface>
```

- Replace `<interface>` with the name of the network interface (e.g, eth0). This command flushes the ARP cache of the specific network interface.

# arp-scan command
1. **Scan Local Network**
```bash
$ sudo arp-scan --localnet

or

$ sudo arp-scan -l
```

2. **Scan Specific Network Range:**
```bash
$ sudo arp-scan <network-range>
```

3. **Scan Specific Interface:**
```bash
$ sudo arp-scan --interface=<interface> <network-range>
```

4. **Specify Number of Packets to send:**
```bash
$ sudo arp-scan --count=<count> <network_range>
```






















