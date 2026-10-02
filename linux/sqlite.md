# sqlite

`sqlite3` opens one database file. No server.

```bash
$ sudo pacman -S sqlite
$ sqlite3 notes.db
```

Inside the shell, SQL ends with a semicolon. Commands that start with a dot are sqlite's own.

```text
CREATE TABLE note (id INTEGER PRIMARY KEY, body TEXT);
INSERT INTO note (body) VALUES ('hello');
SELECT * FROM note;
.tables
.schema
.quit
```

`.tables` lists tables. `.schema` prints the `CREATE` statements. `.quit` closes the file. The database is the file `notes.db` in the directory where you started `sqlite3`.
