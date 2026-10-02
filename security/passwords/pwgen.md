# pwgen

pwgen prints passwords. It does not store them. KeePassXC and `pass` are the stores.

```bash
$ sudo pacman -S pwgen
$ pwgen
$ pwgen -s 20 5
$ pwgen -sy 20 1
```

With no arguments, pwgen prints pronounceable passwords. `-s` switches to random characters. The first number is the length. The second number is how many to print. `-y` puts at least one symbol in each password.
