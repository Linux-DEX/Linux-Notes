# Introduction
+ Hydra is a popular password-cracking tool used to perform brute-force attacks on login credentials for various network services, including FTP, SHH, HTTP, Telnet, MySQL, SMB, and more. 

## Basic Syntax
```bash
$ hydr [options] <service>://<target> <options>
```

+ **Where:**
   - < service >     : Specifies the service protocol to attack (e.g ftp,ssh,http-get).
   - < target >      : Specifies the target IP address or hostname.
   - < options >    : Additional options specific to the selected service.

## Important Options
### General Options
+ **-h, --help**                                        : Display help information.
+ **-l < LOGIN >, --login < LOGIN >**  : Specify a single username.
+ **-L < FILe >, --userlist < FILE >**       : Specify a file containing a list of usernames.
+ **-P, --passlist < FILE >**                      : Specify a file containing a list of passwords.
+ **-o, --output < FILE >**                      : Write cracked passwords to a file.
+ **-t, --threads < NUM >**                    : Set the number of parallel tasks (default is 16).
+ **-v, --verbose**                                    : Increase verbosity level.
+ **-V, --version**                                     : Display version information.

### Service-Specific Options
+ **FTP** : 
    - **-e, --e < s >**                                  : Disable EHLO and just use HELO.
+ **SSH** : 
    - **-I, --ssh-private-key-file < KEY >** : Use the specified private key file.
+ **HTTP**: 
    - **-M, --method < METHOD >**          : Specify HTTP method (e.g., GET, POST).
    - **-C, --cookie < COOKIE >**                : Set a cookie for the request.
    - **-x, --proxy < PROXY >**                    : Use a proxy server for the request.

### Password Attack Options
   + **-x, --x < min:max:charasets >**    : Brute force generation.
   + **-w, --w < FILE >**                          : Load passwords from FILE.
   + **-e, --e < ns >**                               : Stop guessing when a certain number of consecutive erros occur.

# Example
1. **Brute force Attack on FTP.**
```bash
$ hydra -l <username> -P <password_file> ftp://<target_ip>
```

> [!NOTE]
> Password file can be any text file
> for example: /usr/share/wordlist/fasttrack.txt

2. **Brute Force Attack on SSH.**
```bash
$ hydra -l <username> -P <password_file> ssh://<target_ip>

$ hydra -l user -P /usr/share/wordlist/fasttrack.txt ssh://192.168.111.129
```

3. **Brute Force Attack on HTTP POST Request**
```bash
$ hydra -l <username> -P <password_file> -M POST http://<target_ip>/login.php
```

4. **Using Userlist and password list**
```bash
$ hydra -L <userlist_file> -P <password_file> ftp://<target_ip>
```

5. **Output Results to a file**
```bash
$ hydra -l <username> -P <password_file> ftp://<target_ip> -o output.txt
```

6. **Brute force Generation with specific Length and Charset**
```bash
$ hydra -l <username> -x 6:8:aA1 ftp://<target_ip>
```

7. **Specify Number of Threads**
```bash
$ hydra -l <username> -P <password_file> -t 32 ftp://<target_ip>
```

















