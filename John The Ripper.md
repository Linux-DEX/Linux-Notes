# Introduction

+ **John** is a widely-used open-source password-cracking tool designed for various platforms, including Linux.
+ It is primarily used by security professionals, system administrators, and penetration testers to audit password security, recover lost or forgotten passwords, and assess the strength of authentication mechanisms.

# Install the John
```bash
$ pacman -S john
```

## Help command
```bash
$ john -h
```

# Use John the Ripper
There is three modes
   + Single crack mode
   + Wordlist mode
   + Incremental mode

# Single Crack Mode
+ In single-crack mode, John takes a string and generates variations of that string in order to generate a set of passwords.
+ For example, If our username is "stealth" and the password is "StEaLtH", we can use the single mode of john to generate password variations(STEALTH, Stealth, STealth, and so on).
+ We use the "format" flag to specify the hash type and the "single" flag to let john know we want to use the single crack mode.

```bash
stealth:d776dd32d662b8efbdf853837269bd725203c579
```

+ John's single crack mode:
```bash
$ john --single --format=raw-sha1 crack.txt
```

![single crack mode](./img/singlecrackmode.png)

# Dictionary Mode
+ In dictionary mode, we will provide john with a list of passwords. John will generate hashes for these on the fly and compare them with our password hash.
+ For this example, we will use the RockYou wordlist. It can be find in the */usr/share/wordlists/rockyou.txt.*

```bash
$ edba955d0ea15fdef4f61726ef97e5af507430c0
```

+ **dictionary mode using the wordlist:**
```bash
$ john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-sha1 crack.txt
```

# Incremental Mode
+ Incremental mode is the most powerful mode provided by john. It tries all possible character combinations as passwords.
+ This is a problem. The cracking can go on for a long time if the password is too long or if it's a combination of alphanumeric characters and symbols.

+ **Incremental mode:**
```bash
$ john -i:digits passwordfile.txt
```

> [!NOTE]
> + -i  : use th increment mode.
> + digits  : placeholder can be used to set the maximum number of digits in the password.
> + *you can also add the format option to make it easier for john to start cracking.*

# How to Crack a Window Password
+ In Windows, the password hashes are stored in the =SAM database=.
+ SAM uses the LM/NTLM hash format for passwords.

```bash
$ john --format=lm crack.txt
```

   - the crack.txt will contain the password hash.
   - you can use --wordlist flag.

# How to Crack a Linux Password
+ In Linux, there are two important files saved in the etc/ folder: passwd and shadow.
   - `/etc/passwd`   : stores information like username, user id, login shell, and so on.
   - `/etc/shadow`   : contains password hash, password expiry, and so on.

+ unshdow command combines the passwd and shadow file together into a single file.
```bash
$ unshadow /etc/passwd /etc/shadow > output.db
```

+ crack the output.db file using john
```bash
$ john output.db
```

# How to crack a Zip file password
+ John has another utility called =zip2john=. it help us to get the hash from zip file.
+ If you are cracking a .rar file, you can use the rar2john utility.

```bash
$ zip2john file.zip > zip.hashes
```

+ crack the hash using john
```bash
$ john zip.hashes
```



































