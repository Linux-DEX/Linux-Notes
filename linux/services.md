# Apache Service
httpd - Apache Hypertext Transfer Protocol Server

+ Install Apache:
```bash
$ sudo pacman -S apache
```

+ Start Apache
```bash
$ sudo systemctl start httpd
```

+ Stop Apache:
```bash
$ sudo systemctl stop httpd
```

+ Restart Apache:
```bash
$ sudo systemctl restart httpd
```

+ Enable Apache to start on boot:
```bash
$ sudo systemctl enable httpd
```

+ Disable Apache from starting on boot:
```bash
$ sudo systemctl disable httpd
```

+ Check Apache status:
```bash
$ sudo systemctl status httpd
```

+ Reload Apache configuration without restarting:
```bash
$ sudo systemctl reload httpd
```

+ Test Apache configuration for syntax errors:
```bash
$ sudo apachectl configtest
```

+ Open the Apache configuration file in a text editor
```bash
$ sudo nvim /etc/httpd/conf/httpd.conf
```

# Enable SSH
OpenSSH daemon

+ Install OpenSSH:
```bash
$ sudo pacman -S openssh
```

+ Start the SSH service:
```bash
$ sudo systemctl start sshd
```

+ Enable SSH to start on boot:
```bash
$ sudo systemctl enable sshd
```

+ Check the status of the SSH service:
```bash
$ sudo systemctl status sshd
```

# SSH server

The block above only starts `sshd`. These settings are `/etc/ssh/sshd_config`.

Confirm key login in a second terminal before you turn passwords off. A mistake here drops the session you are using to fix it.

```text
PermitRootLogin no
PasswordAuthentication no
KbdInteractiveAuthentication no
PubkeyAuthentication yes
```

`PasswordAuthentication` alone is not enough. Keyboard-interactive still accepts a password unless `KbdInteractiveAuthentication` is off too.

Check the file, then reload. `sshd -t` prints nothing when the config is valid.

```bash
$ sudo sshd -t
$ sudo systemctl reload sshd
```

`ssh-audit` grades this config. `fail2ban` bans addresses that keep failing login. Both notes are under `security/auditing/`.

The client side, keys and `~/.ssh/config`, is the next section.


# SSH client
The section above only starts the server. These commands are for connecting out.

## Connect
```bash
$ ssh user@host
$ ssh -p 2222 user@host
```

## Key instead of a password
```bash
$ ssh-keygen -t ed25519 -C "laptop"
$ ssh-copy-id user@host
```

The private key stays in `~/.ssh/id_ed25519`. The public key is the `.pub` file, and `ssh-copy-id` appends it to `~/.ssh/authorized_keys` on the server.

## Per-host settings
`~/.ssh/config`:

```text
Host lab
    HostName 192.168.1.20
    User archie
    IdentityFile ~/.ssh/id_ed25519
```

Then `ssh lab` uses that block.

## Copy files
```bash
$ scp file.txt lab:/home/archie/
$ rsync -a --info=progress2 ./project/ lab:/home/archie/project/
```

`rsync -a` keeps permissions and skips files that are already the same. Add `--delete` only when the remote directory should become an exact copy.
