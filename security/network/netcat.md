# Introduction
+ **Netcat** or NC is a utility tool that uses TCP and UDP connections to read and write in a network. 
+ It can be used for both attacking and security.
+ In case of attacking. It helps us to debug the network along with investigating it. It runs on all operating system.

# Netcat Tool
## Basic usages:
+ **connect to somewhere:**  
```bash
netcat [options] hostname port [port] ...
```

+ **listen for inbound:**    
```bash
netcat -l -p port [options] [hostname] [port] ...
```

+ **tunnel to somewhere:**
```bash
netcat -L hostname:port -p port [options]
```

## Options:

| Options                   | Description                                  |
| ------------------------- | -------------------------------------------- |
| -c, --close               | close connection on EOF from stdin           |
| -g, --gateway=LIST        | source-routing hop point[s], up to 8         |
| -h, --help                | display this help and exit                   |
| -i, --interval=SECS       | delay interval for lines sent, ports scanned |
| -l, --listen              | listen mode, for inbound connects            |
| -L, --tunnel=ADDRESS:PORT | forward local port to remote address         |
| -n, --dont-resolve        | numeric-only IP addresses, no DNS            |
| -o, --output=FILE         | output hexdump traffic to FILE (implies -x)  |
| -p, --local-port=NUM      | local port number                            |
| -r, --randomize           | randomize local and remote ports             |
| -s, --source=ADDRESS      | local source address (ip or hostname)        |
| -t, --tcp                 | TCP mode (default)                           |
| -T, --telnet              | answer using TELNET negotiation              |
| -u, --udp                 | UDP mode                                     |
| -v, --verbose             | verbose (use twice to be more verbose)       |
| -V, --version             | output version information and exit          |
| -x, --hexdump             | hexdump incoming and outgoing traffic        |
| -w, --wait=SECS           | timeout for connects and final net reads     |
| -z, --zero                | zero-I/O mode (used for scanning)            |

> [!NOTE]
> Remote port number can also be specified as range. Example: '1-1024'

# Commands
## To perform port listening

```bash
$ nc -l -p 8888
```

```bash
$ nc <ip_address> 8888
```

## Test if a particular TCP port of a remote host is open

```bash
$ nc -vn <ip_address> 5000
```
nc: connect to 192.168.233.208 5000 (tcp) failed: Connection refused

## Send a test UDP packet to a remote host
The command below sends a test UDP packet with 1 second timeout to a remote host at port 5000.
```bash
$ echo -n "foo" | nc -u w1 192.168.1.8 5000
```

## Perform TCP port scanning against a remote host
The command below scans ports in the ranges of[1-1000] and [2000-3000] to check which port(s) are open.
```bash
$ nc -vnz -w 1 192.168.233.208 1-1000 2000-3000
```

## Copy a file (e.g., my.jpg) from hostA.com to hostB.com.
On hostB.com (receiver):
```bash
$ nc -lp 5000 > my.jpg
```

On hostA.com (sender):
```bash
$ nc hostB.com 5000 < my.jpg
```

## Transfer a whole directory (including its content) from hostA.com to hostB.com.
On hostB.com (receiver):
```bash
$ nc -l 5000 | tar xvf -
```

On hostA.com (sender):
```bash
$ tar cvf - /path/to/dir | nc hostB.com 5000
```

## Perform UDP port scanning against a remote host.
```bash
$ nc -vnzu 192.168.1.8 1-65535

Connection to 192.168.1.8 68 port [udp/*] succeeded!
Connection to 192.168.1.8 5353 port [udp/*] succeeded!
Connection to 192.168.1.8 16389 port [udp/*] succeeded!
Connection to 192.168.1.8 38515 port [udp/*] succeeded!
Connection to 192.168.1.8 45103 port [udp/*] succeeded!
```

The above command checks which UDP port(s) of a remote host are open and able to receive traffic.

## Listen on a UDP port and dump received data in text format.
The command below listens on UDP port for incoming messages(line of text).
```bash
$ nc -u localhost 5000
```

Note that this command dies after receiving one message. If you want to receive multiple messages, use `while` loop as follows.

```bash
$ while true; do nc -u localhost 5000; done
```

## Back up a (compressed) hard drive (e.g.,/dev/sdb) to a remote server.
**On a remote server:**
```bash
$ nc -lp 5000 | sudo dd of=/backup/sdb.img.gz
```

**On a local host with a hard drive:**
```bash
$ dd if=/dev/sdb | gzip -c | nc remote_server.com 5000
```

## Restore a hard drive from a compressed disk image stored in a remote server:
+ **On a local host**
```bash
$ nc -lp 5000 | gunzip -c | sudo dd of=/dev/sdb
```

+ **On a remote server with a backup disk image (e.g.,/backup/sdb.img.gz):**
```bash
$ cat /backup/sdb.img.gz | nc my_local_host.com 5000
```

## Server a static web page as a web server
Type the command below to launch a web server that serves `test.html` on port 8000.
```bash
$ while true; do nc -lp 8000 < test.html; done
```

Now go to http://:8000/test.html to access it. Note that in order to use a well known port 80, you will need to run `nc` with root privilege as follows.
```bash
$ while true; do sudo nc -lp 80 < test.html; done
```

## (Insecure) online chat between two hosts
+ **On one host(192.168.233.203):**
```bash
$ nc -lp 5000
```

+ **On another host:**
```bash
$ nc 192.168.233.203 5000
```

After runnning the above commands, anything typed on either host appear on the other host's terminal.

## Launch a "remote shell" which allows you run from local host any commands to be executed on a remote host.
+ **On a remote host(192.168.233.208):**
```bash
$ nc -lp 5000 -e /bin/bash
```

+ **On local host:**
```bash
$ nc 192.168.233.208 5000
```

After running the above command on local host, you can start running any command from local host's terminal. The command will be executed on the remote host, and the output of the command will appear on local host. This setup can be used to create a backdoor on a remote host.

## Create a web proxy for a particular website (e.g., google.com)
```bash
$ mkfifo proxypipe
$ while true; do nc -l 5000 0 proxypipe; done
```

The above commands create a named pip `proxypipe`, and use `nc` to redirect all incoming TCP/5000 connections to http://www.google.com via the bidirectional pipe. With this setup, you can access Google by going to http://127.0.0.1:5000.

## Create an SSL proxy for a particular website(e.g., google.com)
```bash
$ mkfifo proxypipe
$ mkfifo proxypipe2
$ nc -l 5000 -k > proxypipe < proxypipe2 &
$ while true do; openssl s_client -connect www.google.com:443 -quiet < proxypipe > proxypipe2; done
```

The above commands use `nc` to proxy SSL connections to Google.com

## Stream a video file from a server, and client watches the streamed video using mplayer.
+ **On a video server(192.168.233.208):**
```bash
$ cat video.avi | nc -l 5000
```

+ **On a client host:**
```bash
$ nc 192.168.233.208 5000 | mplayer -vo x11 -cache 3000 -
```

## Listen on a TCP port using IPv6 address.
The following command let `nc` use IPv6 address when listening on a TCP port. This may be useful to test IPv6 setup.
```bash
$ nc -6 -l 5000

$ sudo netstat -nap | grep 5000

tcp6       0      0 :::5000                 :::*                    LISTEN      4099/nc
```







