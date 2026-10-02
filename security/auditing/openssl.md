# openssl

openssl inspects certificates and can mint a certificate for a name you control. The package is usually already installed. If `openssl version` fails:

```bash
$ sudo pacman -S openssl
$ openssl version
```

## Read a certificate file

```bash
$ openssl x509 -in cert.pem -noout -subject -issuer -dates
$ openssl x509 -in cert.pem -noout -ext subjectAltName
$ openssl x509 -in cert.pem -noout -text
```

`-noout` skips the PEM dump. `-dates` is not-before and not-after. `-ext subjectAltName` is the DNS names the certificate is valid for. `-text` is the full certificate.

## Read the certificate a port presents

```bash
$ openssl s_client -connect localhost:443 -servername localhost </dev/null
```

`-servername` is the TLS name to request. `</dev/null` closes stdin so the command exits after the handshake. Pipe the certificate out of that output:

```bash
$ openssl s_client -connect localhost:443 -servername localhost </dev/null | openssl x509 -noout -subject -dates
```

## Make a self-signed certificate

```bash
$ openssl req -x509 -newkey rsa:2048 -sha256 -days 365 -nodes \
    -keyout key.pem -out cert.pem -subj "/CN=localhost"
$ chmod 600 key.pem
```

`-nodes` leaves `key.pem` unencrypted, so the mode must be `600`. This certificate is not trusted by browsers until you add it yourself. It is for a service of yours, not a name you do not control.
