# KeePassXC

KeePassXC stores passwords in one encrypted database file. `keepassxc` is the window. `keepassxc-cli` is the same database from the terminal. The other password store in these notes is `pass`, in `linux/password-manager.md`.

```bash
$ sudo pacman -S keepassxc
$ keepassxc
$ keepassxc-cli db-create passwords.kdbx
```

`db-create` asks for the database password. Lose that password and the file cannot be opened.

## Entries

```bash
$ keepassxc-cli add -u <user> passwords.kdbx <entry>
$ keepassxc-cli ls passwords.kdbx
$ keepassxc-cli show -a Password passwords.kdbx <entry>
$ keepassxc-cli clip passwords.kdbx <entry>
$ keepassxc-cli rm passwords.kdbx <entry>
```

`add` asks for the entry password. `ls` prints entry names. `show -a Password` prints that one field. `clip` copies the password to the clipboard and clears it after a few seconds. `rm` deletes the entry.

Each command asks for the database password again.

## A password with no entry

```bash
$ keepassxc-cli generate -L 20
```

`-L` is the length. This only prints a password. It does not save one.
