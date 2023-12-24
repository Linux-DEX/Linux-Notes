# Password Manager
`pass` is a command-line password manager for linux. It is designed to be simple, secure, and extensible. Here are some of the most important commands you can use with **pass**:

# Generate gpg-key 
+ Run this command to generate the gpg key
```bash
$ gpg --full-generate-key
```

+ Select the apropriate choose
+ Then enter the `name` and `email address` , and you can add comment to.
+ Then enter the passphrase to protect your new key.
+ that will generate the gpg key.
  
## To view the gpg key
```bash
$ gpg --list-secret-keys --keyid-format LONG
```

## View and export you public key
```bash
$ gpg --list-keys
```

```bash
$ gpg --armor --export <your-email>
```

# pass command
## Initialize Password Store
Initializes the password store using GPG for encryption.

```bash
$ pass init <gpg-key>
```

## Insert New Password
Adds a new password to the store.

```bash
$ pass insert <path/to/password>
```

```bash
$ pass insert email/gmail
```

## Generate a New Password
Generates a new random password.

```bash
$ pass generate <path/to/password> <length>
```

```bash
$ pass generate social/twitter 16
```

## Display Password
Display the password for the specified entry.

```bash
$ pass <path/to/password>
```

```bash
$ pass email/gmail
```

## Edit Password
Edits the password for the specified entry.

```bash
$ pass edit <path/to/password>
```

```bash
$ pass edit social/twitter
```

## List Passwords
Lists all stored passwords.

```bash
$ pass
```

## Decrypt password
```bash
$ gpg -d facebook.com.gpg

or

$ gpg -d social/facebook.com.gpg
```

> [!NOTE]
> Then enter the *passphrase* to unlock.

## Copy Password to Clipboard
Copies the password to the clipboard.

```bash
$ pass -c <path/to/password>
```

## Generate and copy a password
Generate and copies a new password to the clipboard.

```bash
$ pass -c -n <path/to/password>
```

## Find Password
Search for passwords containing the specified term.

```bash
$ pass find <search-term>
```

## Remove Password
Removes the specified password.

```bash
$ pass rm <path/to/password>
```

## Sync Password Store
Pulls changes from the remote Git repository

```bash
$ pass git pull
```

Pushes changes to the remote Git repository

```bash
$ pass git push
```

## Insert a File as an Attachment
Inserts a file as an attachment to a password entry.

```bash
$ pass insert -m <path/to/password> <file>
```

## Backup Password Store
Pushes changes to a remote Git repository

```bash
$ pass git push origin master
```

## Initialize Git repository for password store
Initializes a Git repository for the password store.

```bash
$ pass git init
```

## Show password tree
Display the password tree, showing the hierarchical structure of password.

```bash
$ pass -t
```

## Import Passwords from another password manager
import password from another password manager.

```bash
$ pass import <password-manager>
```
