# LINUX COMMANDS
## sudo
let us use our account and password to execute system commands with root privileges.
### syntax
```bash
$ sudo [option] [command]
```

| option | function    |
| ------ | ----------- |
| -v     | version     |
| -l     | information |

## whoami
print effective user name

```bash
$ whoami
```

## man
An interface to the system reference manuals

```bash
$ man du
```

## clear
Clear the terminal screen.

```bash
$ clear
```

## pwd
Print the current folder path.

```bash
$ pwd
```

## ls
list directory contents

### Syntax
```bash
$ ls [option] [folder]
```

| option | description                  |
| ------ | ---------------------------- |
| /path  | list the content of the path |
| -l     | long format                  |
| -a     | all file including .file     |
| -h     | human readable               |
| -r     | reverse                      |
| -s     | size                         |

## cd
change directory

### Syntax
```bash
$ cd [directory]
```

| Command         | Description                                     |
| --------------- | ----------------------------------------------- |
| cd Desktop      | move to desktop                                 |
| cd..            | travel back by one directory                    |
| cd or cd~       | go to home directory                            |
| cd ../../OTHERS | go to OTHERS folder by passing parent directory |

## mkdir
Make directories

| Command                       | Description                                 |
| ----------------------------- | ------------------------------------------- |
| mkdir coding                  | make a directory by name coding             |
| mkdir winter summer           | make multiple folder winter and summer      |
| mkdir summer/seeds            | make seed directory inside summer directory |
| mkdir -p summer/seeds/lettuce | make parent directory as needed             |

## touch
Change file timestamp or create empty file.

| Command                   | Description     |
| ------------------------- | --------------- |
| touch note.txt            | empty note file |
| touch note1.txt note2.txt | multiple file   |

## rmdir
remove directory if it is empty.

```bash
$ rmdir coding
```

## rm
Remove file or directories

### Syntax
```bash
$ rm [option] [file]
```

| option  | Description                                       |
| ------- | ------------------------------------------------- |
| -v      | explain what is being done                        |
| -r , -R | remove directories and their contents recursively |
| -i      | prompt before every removal                       |
| -f      | force                                             |

## open
Open file in its default application.

```bash
$ open .                    // open current directory
$ open index.html           // open index.html file
```

## mv
Move (rename) files

| Command                   | Description                                        |
| ------------------------- | -------------------------------------------------- |
| mv jornal.txt journal.txt | rename file, renamed 'jornal.txt' -> 'journal.txt' |
| mv journal.txt stuff/     | it will move journal.txt into stuff folder         |
| mv cake cookie pie stuff/ | move multiple file in stuff folder                 |

| option | Description |
| ------ | ----------- |
| -v     | verbore     |
| -f     | force       |

## cp
Copy files and directoies.

| Command                        | Description                                                             |
| ------------------------------ | ----------------------------------------------------------------------- |
| cp note.txt book.txt           | it make book.txt file and copy content of note.txt to book file         |
| cp note.txt Documents/book.txt | it copy the content of note.txt to book.txt in a directory of Documents |

| option | Description                |
| ------ | -------------------------- |
| -r     | copy directory recursively |

## head
Output the first part of files

| Command             | Description                          |
| ------------------- | ------------------------------------ |
| head note.txt       | print first part of the note.txt     |
| head note.txt -n 20 | print first 20 line of note.txt file |

## tail
Output the last part of files

| Command             | Description                         |
| ------------------- | ----------------------------------- |
| tail note.txt       | print last part of the note.txt     |
| tail note.txt -n 20 | print last 20 line of note.txt file |

## date
Print or set the system date and time

```bash
$ date
```

## redirecting standard output

| Command           | Description                                                        |
| ----------------- | ------------------------------------------------------------------ |
| >                 | redirect                                                           |
| date > today.txt  | redirect the output of date to today.txt file it override the file |
| >>                | redirect and append                                                |
| date >> today.txt | it append to the today.txt file                                    |
| 2>                | to redirect an error we need to use                                |
| 2>&1              | to redirect both error and output                                  |

## cat
Concatenate file and print on the standard output

print the content of note.txt
```bash
$ cat note.txt
```

Print content of multiple file
```bash
$ cat note1.txt note2.txt
```

Number all output line
```bash
$ cat -n note.txt
```

## less
Show content stored inside a file in nice and interactive UI
```bash
$ less note.txt
```

## more
Display content of a file in a terminal.
```bash
$ more note.txt
```

## echo
+ Display the line of text.
```bash
$ echo "hello"
```

+ redirect to config.txt
```bash
$ echo "the centent line" > config.txt
```

+ append
```bash
$ echo "next line" >> config.txt
```

## wc
Print new line, word & byte counts for each file.
```bash
$ wc note.txt
```

| Option | Description     |
| ------ | --------------- |
| -w     | word count      |
| -l     | newline count   |
| -m     | character count |
| -c     | byte count      |

## piping ( | ) 
It is used to combin two or more command together. the output of the first command will be input for second command.

print the number of line of ls output
```bash
$ ls -l | wc
```

Print the number of line in the text.txt and note.txt file combine
```bash
$ cat text.txt note.txt | wc -l
```

## sort
Sort line of text files

### syntax
```bash
$ sort [option] [file]
```

| Option | Description  |
| ------ | ------------ |
| -f     | ignore case  |
| -n     | numeric sort |
| -r     | reverse      |
| -u     | unique       |

## uniq
Report or omit repeated lines.
```bash
$ uniq sname.txt

$ sort sname.txt | uniq
```

| Option | Description                 |
| ------ | --------------------------- |
| -d     | only print duplication line |
| -u     | only print unique line      |
| -c     | number of occurrences       |

```bash
$ sort sname.txt | uniq -d
```

## expansion
+ /home/xander
```bash
$ echo ~            
```

+ path set in the system
```bash
$ echo $PATH
```

+ print user name
```bash
$ echo $USER
```

+ display every file and folder in the current directory
```bash
$ echo *
```

+ all the .txt file in current directory
```bash
$ echo *.txt
```

+ list all the file with .txt
```bash
$ ls -l *.txt
```

+ ? -> anycharacter
```bash
echo *.???
```

+ remove any file with any name with only two letter extention
```bash
$ rm *.??
```

```bash
$ echo {a, b, c}

o/p
a b c

$ echo {a,b,c}.txt
o/p
a.txt b.txt c.txt
```

print all file and diretory with first letter 'f'
```bash
$ echo f*
```

## diff
Compase file line by line.
```bash
$ diff note.txt book.txt
```

## find
find the files in a directory hierarchy.

+ find the file name with extension .js in current directory
```bash
$ find . -name '*.js'
```

+ find the file in /home/xander directory
```bash
$ find /home/xander -name '*.txt'
```

+ find the directory
```bash
$ find . -type d -name '*d+'
```

+ case insensitive
```bash
$ find . -type d -iname '*d+'
```

+ find the file which start with E or F
```bash
$ find . -name 'E*' -or -name 'F*'
```

+ find the file whose size greater than 100k
```bash
$ find -type f -size -100k
```

+ 100k < file < 1M
```bash
$ find . -type f -size +100k -size -1M
```

+ find edited more than 3 days ago
```bash
$ find . -type f -mtime +3
```

\; terminating
+ execute command on each result of search
```bash
$ find . -type f -exec cat {}\;
```

## grep
Print lines that match patterns

### Syntax
grep [option] pattern [file]
grep [option] -e patterns [file]
grep [option] -f pattern_file [file]

```bash
$ grep display style.css
```

| Option | Description |
| ------ | ----------- |
| -n     | line number |
| -c     | context     |
| -r     | recursively |

```bash
$ grep -rE -o "[regEx expression]"
```

## du
Estimate file space usage

```bash
$ du                     // space usege of all file

$ du index.html         // space usage of index file
```

| Option | description    |
| ------ | -------------- |
| -m     | MB             |
| -g     | GB             |
| -h     | human readable |

```bash
$ du -h | sort -h        // space usage & sort in human readable
```

## df
report file system space usege or disk usage

```bash
$ df         // show all file
 
$ df Documents/    // show Documents file
```

## history
Show & manipulate command history.

```bash
$ history
```

## ps
Report a snapshot of the current process

```bash
$ ps

$ ps ax            // all the process
 
$ ps axww         // wrap around
```

## top
display linux process

```bash
$ top
```

## htop
interative process viewer

```bash
$ htop
```

## kill
Terminate a process

```bash
$ kill -l          // list signal name

$ kill [pid]      // process id -> pid

$ kill -9 [pid]  
```

## killall 
kill process by name.

```bash
$ killall -9 node

$ killall [processname]
```

## job, bg & fg
jobs -> print currently running jobs.
bg -> send file to background.
fg -> bring jobs to foreground.

```bash
$ jobs

$ fg 2
 
$ bg 1
```

> [!NOTE]
> where 2 & 1 are jobs number.

## sleep
Delay for a specifield amount of time.

```bash
$ sleep 4         // 4 is in seconds
```

## gzip
Compress files

```bash
$ gzip [filename]       // compress & replace the file, with .gz

$ gzip -k profiet.txt  
```

| Option | Description                                         |
| ------ | --------------------------------------------------- |
| -k     | keep input file during compression                  |
| -d     | decompress                                          |
| -v     | display name and percentage reduction for each file |

## gunzip
expand file

```bash
$ gunzip project.txt.gz
```

## zip & unzip
zip - package & compress(archive) files.
unzip - list, test & extract compressed file in a zip archive

```bash
$ zip archive.zip file1 file2
$ zip -r archive.zip directory
$ unzip -l archive.zip
$ unzip archive.zip
$ unzip archive.zip -d [directory]
```

## tar
An archiving utility.

```bash
$ tar -cf archive.tar index.htm style.css

$ tar -tf archive.tar     // to view content of file

$ tar -xf archive.tar    // to extract the tar file

$ tar -xf archive.tar -C [directory]   // extract into that directory. -C, not -c

$ tar -czf archive.tar.gz file1 file2       // gzip-compressed archive. the suffix is .gz

$ tar -xf archive.tar.gz  
```

| Option | Description |
| ------ | ----------- |
| -c     | to create   |
| -f     | file        |
| -z     | zip         |

## alias
Create a function.

### Syntax
```bash
$ alias [name]=[defination]
```

```bash
$ alias ll='ls -la'
```

## xargs
Buid & execute command line from standard input

```bash
$ cat deadPlayers.txt | xargs rm   // the o/p of cat command will be argument of rm

$ find . -size +1M | xargs ls -lh
```

## ln
Make a links between files

### hard link
A hard link **always points a filename to data on a storage device.**

```bash
$ ln original.txt hardlink.txt
```

### symbolic link
A soft link **always points a filename to another filename, which then points to information on a storage device.**

```bash
$ ln -s original.txt symlink.txt
```

## who
displays the user logged in to the system.

```bash
$ who
```

## su
Switch user

```bash
$ su [username]
```

## passwd
password

```bash
$ passwd
```

## chown
Change file owner & group

### syntax
```bash
$ chown [owner] [file]
```

```bash
$ sudo chown xander /project
```

### syntax
```bash
$ chown [owner]:[group] [file]
```

## chmod
Change file mode bits

```bash
$ chmod g+w file.txt

$ chmod a-w file.txt   // remove write permittion from all
```

| number | file mode |
| ------ | --------- |
| 0      | _ _ _     |
| 1      | _ _ x     |
| 2      | _ w _     |
| 3      | _ w x     |
| 4      | r _ _     |
| 5      | r _ x     |
| 6      | r w _     |
| 7      | r w x     |

```bash
$ chmod 711 file.txt

$ chmod a=r file.txt  // it set all read only   
```

> [!NOTE]
> u - Owner , g - Group , o - Others , a - All(owner, groups, others)

## wget
download the resource

### Syntax
```bash
$ wget [option] [url]
```

### Example
+ save at specific location
```bash
$ wget -p [path] [url]
```

## curl
Download the resources.

### syntax
```bash
$ curl [option] [url]
```

### Example
+ to download the file to your local system
```bash
$ curl [url]>[local-file]
```

## lf
Terminal file manager.

```bash
$ lf
```

## gdu
disk usage

```bash
$ gdu
```

## neofetch
System general information.

```bash
$ neofetch
```

neofetch is unmaintained. The replacement is fastfetch.

```bash
$ fastfetch
```

## lshw
Fetch important hardware information, such as memory, cpu, disk, etc..

```bash
$ sudo lshw
```

+ short summary
```bash
$ lshw short
```

## lscpu
CPU information

```bash
$ lscpu
```

## lsblk
Block device information

```bash
$ lsblk

$ lsblk -a      // all information
```

## lsusb
USB device information

```bash
$ lsusb
```

## ifconfig
Information about all active network interface.

```bash
$ ifconfig
```

| Optoin | Description             |
| ------ | ----------------------- |
| -s     | shortlist               |
| -v     | verbose                 |
| -a     | every network interface |

## free 
View amount of memory available on system.
```bash
$ free
```

## lspci
 Check PCI device

```bash
$ lspci
$ lspci -k
```

`-k` adds the kernel driver in use for each device.

## lsscsi
Check SCSI device

```bash
$ lsscsi
```

## hdparm
Check SATA devices

```bash
$ sudo hdparm /dev/sda1
```

## fdisk
File system information

```bash
$ sudo fdisk -l
```

## dmidecode
Hardware components info

```bash
$ sudo dmidecode -t memory    // memory

$ sudo dmidecode -t system   // system

$ sudo dmidecode -t bios    // bios

$ sudo dmidecode -t processor  // processor
```

## ip 
show / manipulate routing, networking devices, interface and tunnels

### Syntax
```bash
$ ip [Option] OBJECT {COMMAND | help}
```

### example
```bash
$ ip addr
$ ip link
$ ip route
$ ip neigh
```

`ip addr` is the address list (`ip a` is the same command). `ip link` is the interfaces, up or down. `ip route` is the routing table. `ip neigh` is the ARP cache, the same information as `arp -a`.

## hostname
display hostname

```bash
$ hostname
```

+ to display ip address
```bash
$ hostname -I
```

## locate
search for file & directories.

### Syntax
```bash
$ locate [option] [pattern]
```

### example
```bash
$ locate .bashrc
```

## bpytop
Better interactive process view

```bash
$ bpytop
```

## fzf
find the file location

```bash
$ fzf
```

## ripgrep
recursively searches for regex pattern

```bash
$ rg port /etc/ssh/sshd_config

$ rg hello
```

## z oxide
navigate to directories

```bash
$ z config

$ z etc ssh        // command get bact to /etc/ssh

$ zi ssh           // interactive searches with fzf
```

## bat
Rust alternative for cat command

```bash
$ bat
```

## exa
Rust alternative for ls command. The exa project is unmaintained. Install `eza` and use the same flags.

```bash
$ exa
$ eza -la
$ eza --tree
```

## speedtest
Test the internet speed up and down

```bash
$ speedtest
```

## route
The route command is the interface used to access the linux kernel's routing tables.

```bash
$ route [option]
```

| key | Description                          |
| --- | ------------------------------------ |
| -v  | verbose                              |
| -n  | don't resolve names                  |
| -e  | display forwarding information base  |
| -C  | display routing cache instead of FIB |

## uname
uname prints the **kernel** name

```bash
$ uname [option1] [option2]
```

```bash
$ uname
```

| Option | Desription                           |
| ------ | ------------------------------------ |
| -a     | Prints all system information        |
| -s     | prints kernel name                   |
| -n     | prints network node hostname         |
| -r     | print the kernel release number      |
| -v     | print the kernel version             |
| -m     | output the machine architecture type |
| -p     | print the CPU type                   |
| -i     | print hardware platform type         |
| -o     | print the operating system name      |

## nice
run a program with modified scheduling priority

### Syntax
```bash
$ nice [OPTION] [COMMAND [ARG]...]
```

```bash
$ nice -n nice_value command
```

## renice
alter priority of running processes

### Syntax
```bash
$ renice [--priority|--relative] priority [-g|-p|-u] identifier...
```

```bash
$ sudo renice -n nice_value -p process_id
```

## tree
List the content of the directories in a tree like format.

### Syntax
```bash
$ tree [option] [directory]
```

| keys     | description                                                     |
| -------- | --------------------------------------------------------------- |
| -a       | All files are listed including hidden file                      |
| -L level | Descend only level directories deep                             |
| -d       | Display directories only, not files                             |
| -f       | print the full path prefix for each file.                       |
| -h       | print size in a human-readable format                           |
| -p       | print a grand total of file and/or directory size after listing |

+ display the directory tree of the current directory
```bash
$ tree
```
 
+ display the tree for a specific directory:
```bash
$ tree /path/to/directory
```

+ display the tree with a specific depth:
```bash
$ tree -L 2
```

+ Display the tree for a specific directory and save it to a file:
```bash
$ tree /path/to/directory > tree_structure.txt
```

## arp
Manipulate the system ARP cache.

### example
this command with show the ip address link with the MAC address of the system
```bash
$ arp -a 
```

## cut
remove sections from each line of files

### Syntax
```bash
$ cut [OPTION] [FILE]
```

```bash
$ cut -d: -f1 /etc/passwd
$ cut -d: -f1,3 /etc/passwd
$ cut -c1-10 file.txt
```

`-d` is the delimiter. `-f` is the field number. `-c` is a character range.

## time
measure how long a command or block takes

### Syntax
```bash
$ time command
```

### Example
```bash
$ time python main.py
```

## xdg-open
open a file or URL in the user's preferred application

### Syntax
```bash
$ xdg-open {file| url}
```

### example
```bash
$ xdg-open index.html
```

## sensors
print sensors information

### Syntax
```bash
$ sensors [ options ] [ chips ]
$ sensors -s [ chips ]
$ sensors --bus-list
```

### example
```bash
$ sensors
```

## iwconfig
configure a wireless network interface

### example
```bash
$ iwconfig

$ iwconfig wlp3s0
```

## wavemon
A wireless network monitor

```bash
$ wavemon
```

## getfacl
Get file access control lists
```bash
$ getfacl <file_name>
```

## shred
overwrite a file to hide its contents, and optionally delete it

### Syntax
```bash
$ shred [OPTION] file
```

### Example
+ shred the file
```bash
$ shred <file_name>
```

+ shred and remove the file
```bash
$ shred --remove <file_name>
```

## file
Determine file type

```bash
$ file <file_name>
```

## netstat
Print network connections, routing tables, interface statistics, masquerade connections, and multicast member-ships

### Syntax
```bash
$ netstat [options]
```

| options | Description                                     | 
| ------- | ----------------------------------------------- |
| a       | display all connections                         |
| l       | display listening ports                         |
| n       | active connections                              |
| p       | display PID and program name for connections    |
| s       | display network statistics                      |
| r       | display routing table                           |
| tulpn   | show listening sockets with process information |
| 4       | display only IPv4 connections                   |
| 6       | display only IPv6 connections                   |

## sed
Stream editor for filtering and transforming text

### Syntax
```bash
$ sed [options] 'command' <file_name>
```

### example
+ Search and replace
```bash
$ sed 's/pattern/replacement/g' filename
```

+ In-place editing (replace in the same file):
```bash
$ sed -i 's/pattern/replacement/g' filename
```

+ Print specific lines:
```bash
$ sed -n '2,5p' filename
```
 
+ delete line matching a pattern
```bash
$ sed '/pattern/d' filename
```

+ Insert text before or after a line:
```bash
$ sed '/pattern/i\text_to_insert' filename
$ sed '/pattern/a\text_to_insert' filename
```

+ substitute using capture groups
```bash
$ sed 's/\(pattern1\)\(pattern2\)/\2\1/g' filename
```

+ printing line number
```bash
$ sed -n '10,20p' filename
```

+ Delete empty lines
```bash
$ sed '/^$/d' filename
```

## ping
Send ICMP ECHO_REQUEST to network hosts

### Syntax
```bash
$ ping <host_name or IP_address>
```

### Example
+ Specifying number of packets:
```bash
$ ping -c <count> <host_name or IP_address>
```

+ Setting time interval between packets
```bash
$ ping -i <interval> <host_name or IP_address>
```

+ Continuous ping
```bash
$ ping -t <host_name or IP_address>
```

+ IPv6 ping
```bash
$ ping6 <host_name or IP_address>
```

+ Timeout Setting
```bash
$ ping -W <timeout> <hostname_or_IP_address>
```

+ Numeric output
```bash
$ ping -n <hostname_or_IP_address>
```

+ Verbose output
```bash
$ ping -v <hostname_or_IP_address>
```

## seq
Print a sequence of numbers.

### Syntax
```bash
$ seq [OPTION] last

$ seq [OPTION] first last

$ seq [OPTION] first increment last
```

### Example
+ Generate number from 1 to 10
```bash
$ seq 10
```

+ Generate numbers from 5 to 15
```bash
$ seq 5 15
```

+ Generate even number from 2 to 20
```bash
$ seq 2 2 20
```

## fold
Wrap each input line to fit in specified width.

### Syntax
```bash
$ fold [OPTION] [FILE]
```

### Example
+ Wrap lines in a file to fit within a width of 80 columns.
```bash
$ fold -w 80 file.txt
```

+ Wrap lines in a file to fit within a width of 70 columns, breaking only at spaces.
```bash
$ fold -w 70 -s file.txt
```

## readlink
Print resolved symbolic links or canonical file names.

### Syntax
```bash
$ readlink [OPTION] file
```

### Example
+ Print the target of a symbolic link
```bash
$ readlink <path_to_symlink>
```

+ Print the canconicalized absolute pathname of a file
```bash
$ readlink -f <path_to_file>
```

+ Print the canconicalized absolute pathname of an existing file
```bash
$ readlink -e <path-to-file>
```

+ Print the target of a symbolic link quietly
```bash
$ readlink -q <path-to-symlink>
```

## sum
Checksum add count the blocks in a file

### Syntax
```bash
$ sum [OPTION] [FILE]
```

### Example
+ Calculate the checksum of a single file using the default system V sum algorithm
```bash
$ sum filename
```

+ Calculate the checksum of multiple files
```bash
$ sum file1 file2 file3
```

+ calculate the checksum of a file using a specific algorithm
```bash
$ sum -a 256 filename
```

+ Calculate the checksum of a file and suppress error messages about missing files
```bash
$ sum -s filename
```

## pr
Convert text files from printing.

### Syntax
```bash
$ pr [OPTION] [FILE]
```

### Example
+ Print the file with pagination
```bash
$ pr filename
```

+ Double-space the output of a file
```bash
$ pr -d filename
```

+ Set custom page length and width
```bash
$ pr -l 50 -w 80 filename
```

+ Add a custom header to the output
```bash
$ pr -h "custom header" filename
```

+ Use form feeds to separate pages
```bash
$ pr -F filename
```

## dircolors
Color setup for ls

## split
Split a file into pieces

### Syntax
```bash
$ split [OPTION] [FILE [PREFIX]]
```

### Example
+ Split a file into smaller file with a specified number of lines
```bash
$ split -l 100 file.txt
```

+ Split a file into smaller files with a specified number of bytes
```bash
$ split -b 1M file.txt
```

+ Split the file into smaller files with a custom prefix
```bash
$ split -l 500 file.txt output_prefix
```

## dirname
Strip last component from file name.

### Syntax
```bash
$ dirname [OPTION] NAME
```

### Example
+ Extract the directory portion of a file path
```bash
$ dirname <path-to-file.txt>
```

+ Extract the directory portion of multiple file paths
```bash
$ dirname <path-to-file1.txt> <path-to-file2.txt>
```

+ Extract the directory portion of a relative path
```bash
$ dirname <directory-file.txt>
```

## od
Dump files in octal and other formats

# More commands

These were not in the list above.

## which, type, whereis
Find what a name points at.

```bash
$ which ls
$ type ls
$ type -a ls
$ whereis ls
```

`which` prints one path and ignores shell builtins. `type` is the one the shell itself uses, so it shows aliases and builtins. `type -a` prints every match. `whereis` also looks for the man page.

## whatis, apropos
Search the manual without opening it.

```bash
$ whatis ls
$ apropos "disk space"
```

`whatis` is the one-line description. `apropos` searches those lines. If either says nothing is found, the man database is stale:

```bash
$ sudo mandb
```

## printenv, export
```bash
$ printenv
$ printenv PATH
$ export EDITOR=nvim
```

`export` sets a variable for this shell and for programs it starts. It is gone when the shell exits, unless the line is in `~/.bashrc`.

## source
Run a file in the current shell. `. file` is the same command.

```bash
$ source ~/.bashrc
```

A script run as `bash file` cannot change your current directory or your variables. `source` can.

## unalias
```bash
$ unalias ll
$ unalias -a
```

`-a` removes every alias in this shell.

## pushd, popd, dirs
A stack of directories, so `cd -` is not the only way back.

```bash
$ pushd /etc
$ pushd /var/log
$ dirs -v
$ popd
```

## reset
Repairs a terminal after a binary file was printed to it and the characters are garbage.

```bash
$ reset
```

## shutdown, reboot, poweroff
```bash
$ shutdown -h now
$ shutdown -r now
$ shutdown -h +10
$ shutdown -c
$ reboot
$ poweroff
```

`-h` halts. `-r` reboots. `+10` waits 10 minutes. `-c` cancels a pending shutdown. `reboot` and `poweroff` do it immediately.

## timedatectl, hostnamectl, localectl
```bash
$ timedatectl
$ timedatectl list-timezones
$ sudo timedatectl set-timezone Asia/Kolkata
$ hostnamectl
$ localectl
```

`timedatectl` shows the clock and whether NTP is on. `hostnamectl` shows hostname, chassis, and the running kernel. `localectl` shows locale and keymap.

## uptime, w, last
```bash
$ uptime
$ w
$ last
$ last reboot
```

`uptime` is the load average and how long the machine has been up. `w` adds who is logged in and what they are running. `last` reads `/var/log/wtmp` for previous logins.

## pgrep, pkill, pidof, pstree
```bash
$ pgrep -a sshd
$ pidof sshd
$ pstree -sp $$
$ pkill sshd
```

`pgrep -a` prints the pid and the command line. `pkill` sends the same signal `kill` sends, matched by name. Check with `pgrep` first.

## lsof
Which process has a file or a port open.

```bash
$ lsof -p [pid]
$ lsof -i :22
$ fuser -vm /mnt/data
```

`lsof -i :22` lists processes using that TCP or UDP port. `fuser` is the one to run when `umount` says the target is busy.

## timeout, nohup, disown
```bash
$ timeout 10s ping example.com
$ nohup command > out.log 2>&1 &
$ disown
```

`timeout` kills the command if it is still running when the time is up. `nohup` keeps a command running after you log out and ignores the hangup signal. `disown` detaches a job that is already in the background of this shell.

## ulimit
Limits of this shell: open files, process count, core size.

```bash
$ ulimit -a
$ ulimit -n
```

## dmesg
Kernel ring buffer.

```bash
$ dmesg -T
```

`-T` prints human-readable times. If the kernel blocks unprivileged `dmesg`, read the same stream with `journalctl -k` (see `linux/systemd.md`).

## lsmod, modinfo, modprobe
```bash
$ lsmod
$ modinfo [module]
$ sudo modprobe [module]
$ sudo modprobe -r [module]
```

`lsmod` is what is loaded. `modinfo` is the description, file path, and parameters. `modprobe` loads a module and its dependencies. `-r` removes it if nothing is using it.

## nproc, cal
```bash
$ nproc
$ cal
$ cal -3
```

`nproc` is how many CPUs this process is allowed to use. `cal` is a month calendar. `-3` is previous, current, and next month.

## updatedb
`locate` only knows about files from the last database build.

```bash
$ sudo updatedb
$ locate .bashrc
```

## awk
A column tool. Print field 1, split on any whitespace:

```bash
$ awk '{print $1}' file
```

`/etc/passwd` is split on colons:

```bash
$ awk -F: '{print $1, $3}' /etc/passwd
```

Add a column of numbers:

```bash
$ awk '{s += $1} END {print s}' numbers.txt
```

## tr
Translate or delete characters. This reads stdin, not a filename.

```bash
$ tr '[:lower:]' '[:upper:]' < file
$ tr -d '\r' < file
$ tr -s ' '
```

`-d` deletes the set. `-s` squeezes repeated characters down to one. The `\r` form strips Windows line endings.

## tee
Write stdin to a file and also pass it through to the next command.

```bash
$ command | tee file.txt
$ command | tee -a file.txt
```

`-a` appends.

## tac, basename, realpath, stat
```bash
$ tac file.txt
$ basename /etc/passwd
$ basename /var/log/pacman.log .log
$ realpath file.txt
$ stat file.txt
$ stat -c '%a %n' file.txt
```

`tac` prints lines last to first. `basename` strips the directory. The second argument also strips a suffix. `realpath` prints the absolute path with symlinks resolved. `stat -c '%a'` is the permission bits as an octal number.

## namei
Every component of a path, with its permissions. Use it when a path fails and you cannot tell which directory is the problem.

```bash
$ namei -l /etc/fstab
```

## mktemp
An empty file or directory with a unique name. The file is created mode `600`.

```bash
$ mktemp
$ mktemp -d
```

## chattr, lsattr
```bash
$ lsattr file.txt
$ sudo chattr +i file.txt
$ sudo chattr -i file.txt
```

`+i` makes the file immutable. Even root cannot change or delete it until `chattr -i`.

## setfacl
Extra permissions on top of `chmod`. `getfacl` prints them.

```bash
$ setfacl -m u:<user>:rw file.txt
$ setfacl -x u:<user> file.txt
$ setfacl -b file.txt
```

`-m` modifies, `-x` removes one entry, `-b` removes the whole ACL.

## sha256sum
```bash
$ sha256sum file
$ sha256sum file > file.sha256
$ sha256sum -c file.sha256
```

`-c` checks the file against a sum you saved. `md5sum` is the same shape. Use it only when the published checksum is MD5.

## cmp, comm, paste
```bash
$ cmp file1 file2
$ comm file1 file2
$ paste -d, file1 file2
```

`cmp` stops at the first differing byte. `comm` needs both files sorted. Column 1 is only in file 1, column 2 is only in file 2, column 3 is in both. `paste` joins lines side by side.

## column, printf, watch
```bash
$ column -t -s: /etc/passwd
$ printf '%s\n' one two three
$ watch -n 2 df -h
```

`column -t` lines the fields up. `watch` repeats a command. The default gap is 2 seconds. `-d` highlights what changed.

## ss
Sockets. This replaces `netstat`.

```bash
$ ss -tulpn
$ ss -tp
```

`-t` TCP, `-u` UDP, `-l` listening, `-p` process name, `-n` do not resolve hostnames. `-tp` without `-l` is established TCP connections.

## dig, tracepath
```bash
$ dig example.com
$ dig +short example.com
$ dig +short MX example.com
$ tracepath example.com
```

`dig +short` prints only the answer. `tracepath` shows each hop and does not need root. `traceroute` is the older command and usually does.

## fd
A file finder. Simpler than `find` for the common case. Arch package name is `fd`.

```bash
$ fd pattern
$ fd -e md
$ fd pattern ~/projects
```

`-e` limits the extension. The pattern is a regular expression, and the search skips hidden files and gitignored files unless you pass `-H` or `-I`.

## jq
Read JSON.

```bash
$ jq . file.json
$ jq '.name' file.json
$ jq -r '.name' file.json
```

`.` pretty-prints the whole document. `-r` prints a string without quotes.

## parted
Partition tables. Listing only:

```bash
$ sudo parted -l
```

## dd
Copy bytes from `if` to `of`. `of` is overwritten from the first byte.

```bash
$ sudo dd if=/dev/sdb of=disk.img bs=4M status=progress conv=fsync
```

`bs` is the block size. `status=progress` prints progress. `conv=fsync` flushes the file before `dd` exits. Check `of` twice. A wrong disk name there destroys that disk.

## sync
Flush pending disk writes.

```bash
$ sync
```

## script
Record a terminal session to a file. `exit` stops the recording.

```bash
$ script session.log
```

## strings, ldd
```bash
$ strings file | less
$ ldd /usr/bin/ls
```

`strings` prints the readable text inside a binary. `ldd` prints the shared libraries that program loads.

