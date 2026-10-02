# age

age encrypts a file. The package also installs `age-keygen`.

```bash
$ sudo pacman -S age
```

## Passphrase

```bash
$ age -p -o secret.txt.age secret.txt
$ age -d -o secret.txt secret.txt.age
```

`-p` asks for a passphrase. `-o` is the output file. `-d` decrypts. The original `secret.txt` is not deleted.

## A key

```bash
$ age-keygen -o key.txt
$ age -r <public-key> -o secret.txt.age secret.txt
$ age -d -i key.txt -o secret.txt secret.txt.age
```

`age-keygen` prints the public key and writes the secret key to `key.txt`. `-r` is that public key, the recipient. `-i` is the secret key file used to decrypt. `key.txt` is not a file to commit. `chmod 600 key.txt` if the umask did not already keep it private.
