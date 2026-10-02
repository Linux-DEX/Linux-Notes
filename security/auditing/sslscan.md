# sslscan

sslscan connects to a TLS port and lists the protocol versions and ciphers that port accepts. Use it on a service you administer. The SSH equivalent is `security/auditing/ssh-audit.md`.

```bash
$ sudo pacman -S sslscan
$ sslscan localhost:443
$ sslscan --show-certificate <host>:<port>
```

The host and port are the service, `localhost:443` or a name you run. `--show-certificate` adds the certificate subject, issuer, and dates.

A line marked weak or a protocol older than TLS 1.2 is the server configuration. Change that service's TLS settings and scan again. sslscan does not change the server.
