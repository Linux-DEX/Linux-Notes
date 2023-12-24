# Introduction
+ Nikto is an open source web server and web application scanner.
+ Nikto can perform comprehensive tests against web servers for multiple security threats, including over 6700 potentially dangerous file/ programs.
+ Nikto can also perform checks for outdated web servers software, and version-specific problems.

# Commands
1. **Help command for nikto:**
```bash
$ nikto --help
```

2. **Scan a domain using =-h= (host) flag:**
```bash
$ nikto -h scanme.nmap.org
```

3. **Scan a Domain with SSL Enabled:**
```bash
$ nikto -h https://nmap.org -ssl
```

4. **Scan an IP Address:**
```bash
$ nikto -h 45.33.32.123
```

5. **Scan multiple IP Address from a Text File:**
```bash
$ nikto -h domains.txt
```

+ The text file should contain domain or ip address to scan.

6. **Save the Scan Result to file:**
```bash
$ nikto -h scanme.nmap.org -o scan.txt
```

- can use `-Format` flag to specify an output format. example format csv, html, nbe, sql, txt,xml.
```bash
$ nikto -h scanme.nmap.org -o scan.csv -Format csv
```

7. **Pair Nikto with metasploit:**
```bash
$ nikto -h <domain/ip> -Format msf+
```

- append the `-Format msf+` flag to the end of a scan.