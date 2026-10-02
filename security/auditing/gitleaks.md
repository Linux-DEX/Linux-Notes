# gitleaks

gitleaks searches a Git repository for secrets: API keys, private keys, and tokens committed by mistake.

```bash
$ sudo pacman -S gitleaks
$ gitleaks detect --source .
$ gitleaks detect --source . --verbose
```

`.` is the repository you are in. `detect` walks the Git history, not only the current files. The exit status is 1 when it finds something. `--verbose` prints the file, the commit, and the rule name.

Check what is staged, before you commit:

```bash
$ gitleaks protect --staged
```

A finding means that string is in the history. Deleting the file in a new commit does not remove it. Rotate the credential, then rewrite or abandon the leaked commit. gitleaks does not rotate it for you.
