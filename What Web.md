# Introduction
+ WhatWeb is a web scanning tool used to identify technologies used on websites.
+ It can analyze a website and provide information about the web server, CMS(Content Management System), frameworks, programming language, and more.

## Basic Syntax
```bash
$ whatweb [options] <URL>
```

# Important Options
## Output Options
+ **-v, --verbose**                      : Increase verbosity level.
+ **-q, --quiet**                          : Suppress all output except errors.
+ **-o, --log-file < FILE >**        : Save output to a log file.

## Scanning Options
+ **--aggression, -a=LEVEL**	              : Set the aggression level. Default: 1
+ **-t num, --max-threads num**          : Number of simultaneous threads.
+ **-U, --user < USERNAME >**            : Specify HTTP basic authentication username.
+ **-P, --password < PASSWORD >**    : Specify HTTP basic authentication password.
+ **-x, --exclude < STRING >**              : Exclude plugins matching the specified string.

## Plugin Options
+ **-e, --enumerate < STRING >**      : Enumerate plugins matching the specified string.
+ **-l, --list-plugins**                            : List available plugins.
+ **-p, --plugins < PLUGINS >**          : Specify plugins to use (comma-separated list).

# Example
1. **Scan a website**
```bash
$ whatweb example.com
```

2. **Scan a website and save output to a file**
```bash
$ whatweb example.com -o output.txt
```

3. **Set the aggression level:**
```bash
$ whatweb -a 3 example.com 
```

4. **Scan a website using HTTP basic Authentication**
```bash
$ whatweb example.com -U username -P password
```

5. **List available plugins**
```bash
$ whatweb -l
```

6. **Scan a website using specific plugin**
```bash
$ whatweb example.com -p whois, WordPress
```

7. **Scan a website and output results in JSON format**
```bash
$ whatweb example.com -j
```





