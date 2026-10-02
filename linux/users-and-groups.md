# Users and groups

## Who you are

```bash
$ id
$ whoami
$ groups
$ getent passwd <user>
$ getent group <group>
```

`getent` reads the same account database login uses, including anything configured in `nsswitch.conf`. `cat /etc/passwd` misses network accounts.

## The three files

| File | Contents |
| ---- | -------- |
| `/etc/passwd` | Name, uid, primary gid, comment, home, shell. The password column is `x` |
| `/etc/shadow` | Password hash and aging. Root can read it. Everyone else cannot |
| `/etc/group` | Group name, gid, and extra members |

A passwd line is seven colon-separated fields:

```text
name:x:uid:gid:comment:home:shell
```

`/etc/sudoers` decides who may run `sudo`. Change it with `sudo visudo`. A syntax error in a hand-edited sudoers file locks sudo out.

## New account on Arch

```bash
$ sudo useradd -m -G wheel -s /bin/bash <user>
$ sudo passwd <user>
```

`-m` creates the home directory from `/etc/skel`.

Membership in `wheel` does nothing until this line is uncommented with `visudo`:

```text
%wheel ALL=(ALL:ALL) ALL
```

That line is already in the default sudoers file, commented out.

## Change an account

```bash
$ sudo usermod -aG <group> <user>
$ sudo usermod -s /bin/fish <user>
$ sudo chsh -s /bin/fish <user>
```

`-aG` appends one supplementary group. `-G` without `-a` replaces the supplementary group list.

A group added while you are logged in does not apply to that session. Log in again, or run `newgrp <group>`.

## Remove an account

```bash
$ sudo userdel <user>
$ sudo userdel -r <user>
```

`-r` also deletes the home directory and mail spool.

## Groups

```bash
$ sudo groupadd <group>
$ sudo gpasswd -a <user> <group>
$ sudo gpasswd -d <user> <group>
```

## umask

```bash
$ umask
```

`022` masks the write bit for group and other. New files are created `644`, new directories `755`, before any program tightens them further.
