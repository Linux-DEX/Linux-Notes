# What is Nmap
Nmap -> Network Mapper.

+ Nmap is a free and open source utility for network discovery and security auditing. 
+ Many systems and network administrators also find it useful for tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime.
+ Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running.
+ It was designed to rapidly scan large networks, but works fine against single hosts.

# How to Use Nmap
Nmap can be used in a variety of ways depending on the user's level of technical expertise.

| Technical Expertise | Usage                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------- |
| Beginner            | [Zenmap](https://nmap.org/zenmap) the graphical user interface for Namp               |
| Intermediate        | [Command line](https://nmap.org)                                                      |
| Advanced            | Python scripting with the [Python-nmap](https://pypi.org/project/python-nmap) package |

## Command line
```bash
$ nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }
```

# Basic Scanning Techniques
The `-s` switch determines the type of scan to perform.

| Nmap Switch | Description                |
| ----------- | -------------------------- |
| -sA         | ACK scan                   |
| -sF         | FIN scan                   |
| -sI         | IDLE scan                  |
| -sL         | DNS scan (a.k.a list scan) |
| -sN         | NULL scan                  |
| -sO         | Protocol scan              |
| -sP         | Ping scan                  |
| -sR         | RPC scan                   |
| -sS         | SYN scan                   |
| -sT         | TCP connect scan           |
| -sW         | Windows scan               |
| -sX         | XMAS scan                  |

## Scan a Single Target
```bash
$ nmap [target]
```

## Scan Multiple Targets
```bash
$ nmap [target1, target2, etc]
```

## Scan a List of Targets
```bash
$ nmap -iL [list.txt]
```

## Scan a Range of Hosts
```bash
$ nmap [range of IP addresses]
```

## Scan an Entire Subnet
```bash
$ nmap [ip address/cdir]
```

## Scan Random Hosts
```bash
$ nmap -iR [number]
```

## Exclude Targets From a Scan
```bash
$ nmap [targets] --exclude [targets]
```

## Exclude Targets Using a List
```bash
$ nmap [targets] --excludefile [list.txt]
```

## Perform an Aggresive Scan
```bash
$ nmap -A [target]
```

## Scan an IPv6 Target
```bash
$ nmap -6 [target]
```

# Port Scanning Options
## Perform a Fast Scan
```bash
$ nmap -F [target]
```

## Scan Specific Ports
```bash
$ nmap -p [port(s)] [target]
```

## Scan Ports by Name
```bash
$ nmap -p [port name(s)] [target]
```

## Scan Ports by Protocol
```bash
$ nmap -sU -sT -p U:[ports],T:[ports] [target]
```

## Scan All Ports
```bash
$ nmap -p 1-65535 [target]
```

## Scan Top Ports
```bash
$ nmap --top-ports [number] [target]
```

## Perform a sequential Port Scan
```bash
$ nmap -r [target]
```

## Attempt to Guess an Unknown OS
```bash
$ nmap -o --osscan-guess [target]
```

## Service Version Detection
```bash
$ nmap -sV [target]
```

## Troubleshoot Version Scan
```bash
$ nmap -sV --version-trace [target]
```

## Perform a RPC Scan
```bash
$ nmap -sR [target]
```

# Discovery Options
**Host Discovery** The `-p` switch determines the type of ping to perform.

| Nmap Switch | Description |
| ----------- | ----------- |
| -PI         | ICMP ping   |
| -Po         | No ping     |
| -PS         | SYN ping    |
| -PT         | TCP ping    |

## Perform a Ping Only scan
```bash
$ nmap -sn [target]
```

## Do Not Ping
```bash
$ nmap -Pn [target]
```

## TCP SYN Ping
```bash
$ nmap -PS [target]
```

## TCP ACK Ping
```bash
$ nmap -PA [target]
```

## UDP Ping
```bash
$ nmap -PU [target]
```

## SCTP INIT Ping
```bash
$ nmap -PY [target]
```

## ICMP Echo Ping
```bash
$ nmap -PE [target]
```

## ICMP Timestamp Ping
```bash
$ nmap -PP [target]
```

## ICMP Address Mask Ping
```bash
$ nmap -PM [target]
```

## IP Protocol Ping
```bash
$ nmap -PO [target]
```

## ARP ping
```bash
$ nmap -PR [target]
```

## Traceroute
```bash
$ nmap --traceroute [target]
```

## Force Reverse DNS Resolution
```bash
$ nmap -R [target]
```

## Disable Reverse DNS Resolution
```bash
$ nmap -n [target]
```
 
## Alternative DNS Lookup
```bash
$ nmap --system-dns [target]
```

## Manually specify DNS Server
Can specify a single server or multiple.
```bash
$ nmap --dns-servers [servers] [target]
```

## Create a Host List
```bash
$ nmap -sL [targets]
```

# Script scan 

| Nmap Switch                               | Description             |
| ----------------------------------------- | ----------------------- |
| -sC                                       | Run all default scripts |

# Timing and Performance 
The `-t` switch determines the speed and stealth performed.

| Nmap Switch | Description                 |
| ----------- | --------------------------- |
| -T0         | Serial, slowest scan        |
| -T1         | Serial, slow scan           |
| -T2         | Serial, normal speed scan   |
| -T3         | Parallel, normal speed scan |
| -T4         | Parallel, fast scan         |

Not specifying a `T` value will default to `-T3`, or normal speed.

# Firewall Evasion techniques
## Fragment Packets
```bash
$ nmap -f [target]
```

## Specify a Specific MTU
```bash
$ nmap --mtu [MTU] [target]
```

## Use a Decoy
```bash
$ nmap -D RND:[number] [target]
```

## Idle Zombie Scan
```bash
$ nmap -sI [zombie] [target]
```

## Manually Specify a Source Port
```bash
$ nmap --source-port [port] [target]
```

## Append Random Data
```bash
$ nmap --data-length [size] [target]
```

## Randomize Target Scan Order
```bash
$ nmap --randomize-hosts [target]
```

## Spoof MAC Address
```bash
$ nmap --spoof-mac [MAC|0|vendor] [target]
```

## Send Bad Checksums
```bash
$ nmap --badsum [target]
```

# Advanced Scanning Functions
## TCP SYN Scan
```bash
$ nmap -sS [target]
```

## TCP Connect Scan
```bash
$ nmap -sT [target]
```

## UDP Scan
```bash
$ nmap -sU [target]
```

## TCP NULL Scan
```bash
$ nmap -sN [target]
```

## TCP FIN Scan
```bash
$ nmap -sF [target]
```

## Xmas Scan
```bash
$ nmap -sA [target]
```

## TCP ACK Scan
```bash
$ nmap -sA [target]
```

## Custom TCP Scan
```bash
$ nmap --scanflags [flags] [target]
```

## IP Protocol Scan
```bash
$ nmap -sO [target]
```

## Send raw Ethernet Packets
```bash
$ nmap --send-eth [target]
```

## Send IP Packets
```bash
$ nmap --send-ip [target]
```

# Timing Options
## Timing Templates
```bash
$ nmap -T[0-5] [target]
```

## Set the Packet TTL
```bash
$ nmap -ttl [time] [target]
```

## Minimum Number of Parallel Operations
```bash
$ nmap --min-parallelism [number] [target]
```

## Maximum Number of Parallel Operations
```bash
$ nmap --max-parallelism [number] [target]
```

## Minimum Host Group Size
```bash
$ nmap --min-hostgroup [number] [targets]
```

## Maximum Host Group Size
```bash
$ nmap --max-hostgroup [number] [targets]
```

## Maximum RTT Timeout
```bash
$ nmap --initial-rtt-timeout [time] [target]
```

## Initial RTT Timeout
```bash
$ nmap --max-rtt-timeout [TTL] [target]
```

## Maximum Number of Retries
```bash
$ nmap --max-retries [number] [target]
```

## Host Timeout
```bash
$ nmap --host-timeout [time] [target]
```

## Minimum Scan Delay
```bash
$ nmap --scan-delay [time] [target]
```

## Maximum Scan Delay
```bash
$ nmap --max-scan-delay [time] [target]
```

## Minimum Packet Rate
```bash
$ nmap --min-rate [number] [target]
```

## Maximum Packet Rate
```bash
$ nmap --max-rate [number] [target]
```

## Defeat Reset Rate Limits
```bash
$ nmap --defeat-rst-ratelimit [target]
```

# Output Options
 
| Nmap Switch | Description                                  |
| ----------- | -------------------------------------------- |
| =-oN=       | Normal output                                |
| =-oX=       | XML output                                   |
| =-oA=       | Normal, XML, and Grepable format all at once |

## Save Output to a Text File
```bash
$ nmap -oN [scan.txt] [target]
```

## Save Output to a XML File
```bash
$ nmap -oX [scan.xml] [target]
```

## Grepable Output
```bash
$ nmap -oG [scan.txt] [target]
```

## Output All Supported File Types
```bash
$ nmap -oA [path/filename] [target]
```

## Periodically Display Statistics
```bash
$ nmap --stats-every [time] [target]
```

## 1337 Output
```bash
$ nmap -oS [scan.txt] [target]
```

# Compare Scans
## Comparison Using Ndiff
```bash
$ ndiff [scan1.xml] [scan2.xml]
```

## Ndiff Verbose Mode
```bash
$ ndiff -v [scan1.xml] [scan2.xml]
```

## XML Output Mode
```bash
$ ndiff --xml [scan1.xml] [scan2.xml]
```

# Troubleshooting and Debugging
## Get Help
```bash
$ nmap -h
```

## Display Nmap Version
```bash
$ nmap -V
```

## Verbose Output
```bash
$ nmap -v [target]
```

## Debugging
```bash
$ nmap -d [target]
```

## Display Port State Reason
```bash
$ nmap --reason [target]
```

## Only Display Open Ports
```bash
$ nmap --open [target]
```

## Trace Packets
```bash
$ nmap --packet-trace [target]
```

## Display Host Networking
```bash
$ nmap --iflist
```

## Specify a Network Interface
```bash
$ nmap -e [interface] [target]
```

# Nmap Scripting Engine
## Execute individual Scripts
```bash
$ nmap --script [script.nse] [target]
```

## Execute Multiple Scripts
```bash
$ nmap --script [expression] [target]
```

## Execute Scripts by Category
```bash
$ nmap --script [category] [target]
```

## Execute Multiple Script Categories
```bash
$ nmap --script [category1,category2,etc]
```

## Troubleshoot Scripts
```bash
$ nmap --script [script] --script-trace [target]
```

## Update the script Database
```bash
$ nmap --script-updatedb
```



















