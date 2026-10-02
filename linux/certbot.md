# certbot

certbot gets a TLS certificate from Let's Encrypt for a hostname you control, and renews it. A self-signed certificate made with openssl is in `security/auditing/openssl.md`. This one is signed by a public CA.

```bash
$ sudo pacman -S certbot
$ sudo certbot certonly --webroot -w /srv/http -d <hostname>
$ sudo certbot certificates
$ sudo systemctl enable --now certbot-renew.timer
$ sudo certbot renew --dry-run
```

`--webroot` serves a challenge file from that directory. The hostname's DNS must already point at this machine, and the web server must publish `/srv/http`. The certificate and key land in `/etc/letsencrypt/live/<hostname>/`. `certbot-renew.timer` runs the renewal. `--dry-run` talks to the staging server and does not replace the live certificate.
