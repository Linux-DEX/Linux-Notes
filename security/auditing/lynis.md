# Introduction
+ Lynis is an extensible security audit tool for computer systems running linux, FreeBSD, macOS, OpenBSD, Solaris, and other Unix derivatives.
+ It assists system administrators and security professionals with scanning a system and its security defenses, with the final goal being system hardening.

## Syntax
```bash
$ lynis command [options]
```

## Command:
### audit
| Command                    | Description                  |
| -------------------------- | ---------------------------- |
| audit system               | Perform local security scan. |
| audit system remote <host> | Remote security scan         |
| audit dockerfile <file>    | Analyze Dockerfile           |

### show
| Command      | Description        |
| ------------ | ------------------ |
| show         | Show all commands  |
| show version | Show lynis version |
| show help    | Show help          |

### update
| Command     | Description         |
| ----------- | ------------------- |
| update info | Show update details |

## Options:
### Alternative system audit modes

| Options     | Description                                             |
| ----------- | ------------------------------------------------------- |
| --forensics | Perform forensics on a running or mounted system.       |
| --pentest   | Non-privileged, show points of interest for pentesting. |

### Layout options
| Options           | Description                                   |
| ----------------- | --------------------------------------------- |
| --no-colors       | Don't use colors in output                    |
| --quiet (-q)      | No output                                     |
| --reverse-colors  | Optimize color display for light backgrounds  |
| --reverse-colours | Optimize colour display for light backgrounds |

### Misc options
| Options                  | Description                                            |
| ------------------------ | ------------------------------------------------------ |
| --debug                  | Debug logging to screen                                |
| --no-long                | Don't create a log file                                |
| --profile <profile>      | Scan the system with the given profile file            |
| --view-manpage (--man)   | View man page                                          |
| --verbose                | Show more details on Screen                            |
| --version (-v)           | Display version a set of tests                         |
| --wait                   | Wait between a set of tests                            |
| --slow-warning <seconds> | Threshold for slow test warning in second (default 10) |

### Enterprise options
| Options     | Description                      |
| ----------- | -------------------------------- |
| --plugindir | Define path of available plugins |

# Install and read a scan
```bash
$ sudo pacman -S lynis
$ sudo lynis audit system
```

A root scan writes `/var/log/lynis.log` and `/var/log/lynis-report.dat`. Run as a normal user and those two files land in the current directory instead.

The end of the scan prints a hardening index from 0 to 100, then two lists:

+ **Warnings** are misconfigurations Lynis treats as higher priority.
+ **Suggestions** are hardening steps. Each line has a test id in brackets. Search the log for that id to see the finding.

`--quick` skips the pauses between tests. It does not skip the tests.

## Again, without sitting in front of it

```bash
$ sudo lynis audit system --cronjob
$ grep -E 'warning\[\]|suggestion\[\]|hardening_index' /var/log/lynis-report.dat
```

`--cronjob` is quiet and does not wait between tests. The report file is still written. A timer that runs that command is an ordinary systemd timer, covered in `linux/systemd.md`. 

















