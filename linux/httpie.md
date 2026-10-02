# HTTPie

HTTPie sends HTTP requests and prints the response in color. `curl` is the other client, in `linux/commands.md`. The command name is `http`.

```bash
$ sudo pacman -S httpie
$ http GET https://example.com
$ http https://example.com
$ http -v GET https://example.com/path
```

A URL with no method is a GET. `-v` prints the request headers as well as the response.

POST a JSON object. `key=value` becomes a JSON field. `key:=value` keeps a number or `true` as JSON, not a string.

```bash
$ http POST https://example.com/api name=ada active:=true
$ http GET https://example.com/api Authorization:"Bearer <token>"
```

A header is `Name:value`. The space after the colon is optional.
