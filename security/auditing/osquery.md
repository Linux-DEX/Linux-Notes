# osquery

osquery answers questions about this machine in SQL. `osqueryi` is the interactive shell.

```bash
$ sudo pacman -S osquery
$ sudo osqueryi
```

```text
SELECT username, uid, directory FROM users WHERE uid >= 1000;
SELECT pid, name FROM processes LIMIT 10;
SELECT pid, address, port FROM listening_ports WHERE port > 0;
.tables
.quit
```

End SQL with a semicolon. `.tables` lists the tables this build knows. `.quit` exits. The rows are the live system, not a database file you created.
