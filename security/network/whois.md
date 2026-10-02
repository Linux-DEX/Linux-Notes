# whois

whois prints the published registration record for a domain name or an IP address. That record is what the registrar or the regional registry already makes public.

```bash
$ sudo pacman -S whois
$ whois <domain>
$ whois <address>
```

A domain query returns the registrar, the name servers, and the dates the registration was created and expires. An address query returns the network block and the organization it is assigned to.

The client picks the registry server. There is nothing to configure.
