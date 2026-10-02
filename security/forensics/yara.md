# YARA

YARA scans files against rules you write. A rule is a set of strings and a condition. Kali lists it with the forensics tools. This is how a rule runs, not a malware signature pack.

`rule.yar`:

```text
rule example {
    strings:
        $a = "hello"
    condition:
        $a
}
```

```bash
$ sudo pacman -S yara
$ yara rule.yar file
$ yara -r rule.yar directory
```

If `file` contains `hello`, yara prints `example` and the filename. No match prints nothing. `-r` walks the directory. yara does not delete or quarantine the file.
