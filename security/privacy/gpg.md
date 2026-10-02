# GnuPG files

Creating a key, and using it with `pass`, is `linux/password-manager.md`. This page is encrypting and signing a file.

## Encrypt to yourself

```bash
$ gpg --encrypt --recipient <email> -o file.gpg file
$ gpg --decrypt -o file file.gpg
```

`<email>` is an address already on a public key in your keyring, usually your own. `--decrypt` asks for the passphrase of the matching secret key. The original `file` is not deleted.

## Passphrase, no key

```bash
$ gpg --symmetric -o file.gpg file
$ gpg --decrypt -o file file.gpg
```

`--symmetric` asks for a passphrase and does not use a key. Lose the passphrase and the file cannot be opened.

## Sign

```bash
$ gpg --detach-sign file
$ gpg --verify file.sig file
```

`--detach-sign` writes `file.sig` and leaves `file` unchanged. `--verify` checks that signature against `file` and against the public key. It prints `Good signature` when both match.
