# Introduction
+ Netdiscover is a network scanning tool used to discover active hosts on a network.
+ It works by sending ARP(Address Resolution Protocol) requests and analyzing the responses to map out the devices present on the local network.

## Basic Syntax
```bash
$ netdiscover [options]
```

## Important Options
### General Options
+ **-i < interface >**   : Specify the network interface to use for scanning.
+ **-r < IP range >**    : Specify the IP range to scan (CIDR notation).
+ **-p**                         : Passive mode. Do not send ARP packets; only listen for ARP requests.
+ **-S**                         : Enable silent mode. Do not display any output to the console.
+ **-L**                          : Enable logging. Write results to a log file.

### Output Options
+ **-o < output-file >**    : Save results to a file.
+ **-c < count >**             : Limit the number of packets sent.
+ **-F**                               : Enable fast mode. Do not resolve MAC addresses to vendor names during scanning.
+ **-n node**                      : last source IP octent used for scanning(from 2 to 253).

### Scanning Options:
+ **-r < ip-range >**                           : Specify the IP range to scan(CIDR notation).
+ **-r < ip-range1, ip range2, ... >**   : Specify multiple IP ranges to scan.
+ **-i < interface >**                           : Specify the network interface to use for scanning.

# Example
+ **Scan the Local Network:**
```bash
$ netdiscover
```

+ **Scan a Specific Interface:**
```bash
$ netdiscover -i eth0
```

+ **Scan a Specific IP Range:**
```bash
$ netdiscover -r 192.168.1.0/24
```

+ **Save Results to a File:**
```bash
$ netdiscover -o output.txt
```

+ **Passive Mode(Listen Only):**
```bash
$ netdiscover -p
```

+ **Limit Number of Packets Sent:**
```bash
$ netdiscover -c 50
```

+ **Last source IP octent:**
```bash
$ netdiscover -n 100
```

+ **Fast Mode(No MAC Address Resolution):**
```bash
$ netdiscover -F
```