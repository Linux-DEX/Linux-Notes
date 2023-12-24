# LINUX FILE SYSTEM
Linux file system contains
- The root directory (/).
- A specific data storage format (EXT3, EXT4, BTRFS, XFS & so on).
- A partition or logical volume having a particular file system.

## Directory Structure
###  /
Root file system

### /boot
Include the static kernel and bootloader configuration and executable file needed to start a linux.

### /bin
Executable file

### /dev
Include the device file for all hardware devices connected to the system there aren't device drivers, instead they are files that indicate all devices on the system and provided access to there devices.

### /etc
Include the local system configuration file for the host system.

### /lib
Include shared library files that are needed to start the system.

### /home
Home directory storage is available for user file all users have subdirectory inside /home

### /mnt
Temporary mount point for basic file system.

### /media
Mounting external removable media devices like USB thumb drives that might be linked to the host.

### /opt
Vendor supplied application program that must be placed.

### /root
Its the home directry for a root user.

### /tmp
temporary directory used by the OS and several program for storing temprory file.

### /sbin
These are system binary file they are executable utilized for system administration.

### /usr
They are read only and shareable files, including executable libraries and binaries, man files and several documentation types.

### /var
Variable data files are saved contain MySQL, log file , etc..


## Linux File System features
+ Specifying paths
+ Partition, directories & drives.
+ Case sensitivity.
+ File extensions.
+ Hidden Files.

# TYPES OF LINUX FILE SYSTEM
## Ext, Ext2, Ext3 & Ext4 file system
+ Extended file system
+ The ext4 file system is **a scalable extension of the ext3 file system,** which was the default file system of Red Hat Enterprise Linux 5.
+ Ext4 is the default file system of Red Hat Enterprice Linux 6, and can support file and file systems up to 16 terabytes in size.

## JFS file system
+ Journaled file system
+ stability is needed with few resources.
+ handy file system when CPU power is limited.

## ReiserFS file system
## XFS file system
## BTRFS file system
## swap file system

# Display server protocols 
## X11
+ By design, X11 is **network-transparent**.
+ This allows the possibility of running the client and the server either on the same machine or different ones.
+ A client and a server can also communicate over the internet through an encrypted network session.

  ![x11](./img/x11.png)

## Wayland
+ Wayland is **a communication protocol that specifies the communication between a display server and its clients, as well as a C library implementation of that protocol.**
+ A display server using the wayland protocol is called a wayland compositor, because it additionally performs the task of a compositing window manager.

![wayland](./img/wayland.png)

# Kernel 
+ Kernel is the main component of a linux operating system(OS) and is the core interface between a computer's hardware and it's process.
+ It communicates between the 2, managing resources as efficiently as possible.

## Types of Kernel
### Stable
+ Vanilla Linux kernel and modules, with a few patches applied.
+ The stable kernel is also the default kernel in most linux distributions, and it is supported by the community and the kernel developers.

[stable kernel website](https://www.kernel.org)

### Hardened
+ A security-focused Linux kernel applying a set of hardening patches to mitigate kernel and userspace exploits. It also enable more upstream kernel hardening features the linux.
+ The term kernel hardening refers to a strategy of using specific kernel configuration options to limit or prevent certain types of cyber attacks.

[hardened kernel github](https://githum.com/anthraxx/linux-hardened)

### Longterm
+ Long-term support(LTS) linux kernel and modules.
+ Longterm(LTS) are usually several "longterm maintenance" kernel releases provided for the purpose of backporting bugfixes for older kernel trees.
+ Only important bugfixes are applied to such kernels and they don't usually see very frequent releases, especially for older trees.

[long term kernel website](https://www.kernel.org)

### Zen Kernel
+ Result of a collaborative effort of kernel hackers to provide the best linux kernel possible for everyday systems.
+ Zen-kernel is a series of patches and improvements that were made to the original linux kernel to improve the performance and reactivity of the system.

[zen kernel github](https://github.com/zen-kernel/zen-kernel)
 
### Realtime kernel 
+ Maintained by a small group of core developers led by Ingo Molnar. 
+ This patch allows nearly all of the kernel to be preempted, with the exception of a few very small regions of code.
+ This is done by replacing more kernel spinlocks with mutexes that support priorty inheritance, as well as moving all interrupt and software interrupts to kernel threads.

# Bootloader
+ Boot Loader is **a software program that is responsible for "actually loading" the operating system once the boot manager has finished its work**. And by loading operating system we mean "loading the kernel of the operating system". 
+ For Linux, the two most common boot loaders are known as **LILO(linux LOader) and LOADLIN(LOAD LINux)**.
+ An alternative boot loader, called GRUB(GRand Unified Bootloader), is used with Red Hat Linux.

## Types of Bootloader
### GNU GRUB
+ GNU GRUB (short for GNU GRand Unified Bootloader, commonly referred to as GRUB) is a boot loader package from the GNU project.
+ GRUB is the program of linux systems that **loads and manages the boot process**.
+ It also **lets you easily an entry on the fly, or drop down into the command interface**. In addition, if you are using the menu interface and something goes wrong, GRUB automatically puts you into the command interface so you can attempt to recover and boot menually.
+ GRUB offers several advantages over other boot loaders. **It can boot multiple operating systems, allowing users to select with OS they would like to boot at startup.**. It also supports a variety of file systems, making it compatible with a wide range of storage devices.

![grub image](./img/grub.png)

### systemd-boot
+ systemd-boot is **a free and open-source boot manager created by obsoleting the gummiboot project and merging it into systemd in May 2015**.
+ systemd-boot previously called **gummiboot**, is an easy-to-configure UEFI boot manager. It provied a textual menu to select the boot entry and an editor for the kernel command line. 
+ It is uncomplicated and uses simple text file which only contain a few lines.

  ![systemd boot image](./img/systemd-boot.png)

### rEFInd Boot Manager
### LILO (Linux Loader)
### BURG - New Boot Loader
### Syslinux

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

## tar
An archiving utility.

```bash
$ tar -cf archive.tar index.htm style.css

$ tar -tf archive.tar     // to view content of file

$ tar -xf archive.tar    // to extract the tar file

$ tar -xf archive.tar  -c [directory]   // to extract in other location.

$ tar -czf archive.tar.gy file1 file2       // compressed archive

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
```

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
$ ip a 
```

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
Rust alternative for ls command

```bash
$ exa
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

# RANGER (File Manager)
Terminal file manager

```bash
$ ranger
```

| Keys    | Description                |
| ------- | -------------------------- |
| h j k l | back , down , up , forward |
| gg      | go to the top              |
| i       | preview file               |
| r       | open file                  |
| zh      | view hidden file           |
| cw      | rename current file        |
| yy      | (yank) copyfile            |
| dd      | cut file                   |
| pp      | past file                  |
| u       | undo                       |
| z       | changing settings          |
| dD      | delete file                |

# Changing default shell
## list the shell in system

```bash
$ chsh -l
```

## select the path from the option given

```bash
$ chsh -s /bin/fish
```

# NETWORK MANAGER (to connect to wifi)

## Connect to wifi
```bash
$ nmcli dev wifi connect "<ssid>" password "<password>"
```

## Delete the network
```bash
$ nmcli con delete "<ssid>"
```

## Disconnect
```bash
$ nmcli con down <wifi-name>
```

## Check wifi connection
```bash
$ nmcli con
```

## Check available wifi
```bash
$ nmcli d wifi list
```

## Turn on wifi
```bash
$ nmcli r wifi on
```

## Turn off wifi
```bash
$ nmcli r wifi off
```

## Show password
```bash
$ nmcli device wifi show-password
```

# BLUETOOTH MANAGER
## Check bluetooth status
```bash
$ sudo systemctl status bluetooth
```

## Enable service
```bash
$ sudo systemctl enable bluetooth
```

## Start bluetooth
```bash
$ sudo systemctl start bluetooth
```

## Scan
```bash
$ bluetoothctl scan on
```

## Discoverable to other devices
```bash
$ bluetoothctl discoverable on 
```

## Pair device
```bash
$ bluetoothctl pair <device-id>
```

## Connect device
```bash
$ bluetoothctl connect <device-id>
```

## List pair device
```bash
$ bluetoothctl paired-devices
```

## List devices within bluetooth range
```bash
$ bluetooth devices

$ bluetoothctl <option> <device-id>
```

## option
### trust
### remove
### block
### untrust
### disconnect


# VIM / NEOVIM
## Global
| Command         | description            |
| --------------- | ---------------------- |
| :h[elp] keyword | open help for keyword  |
| :sav[eas] file  | save file as           |
| :clo[se]        | close current pane     |
| :ter[minal]     | open a terminal window |
| :w              | save file              |
| :wq             | save & exit            |
| :q              | exit                   |
| :!q             | exit without saving    |
| :x              | save & exit            |
| ZZ              | save & exit            |
| ZQ              | exit without saving    |
| :qa             | close all files        |

## Cursor Movement
| Command   | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| h         | move cursor left                                                      |
| j         | move cursor down                                                      |
| k         | move cursor up                                                        |
| l         | move cursor right                                                     |
| gj        | move cursor down multi-line text                                      |
| gk        | move cursor up multi-line text                                        |
| H         | move to top of screen                                                 |
| M         | move to middle of screen                                              |
| L         | move to bottom of screen                                              |
| w         | jump forward to the start of word                                     |
| W         | jump forward to the start of a word ( word can contain punctuation )  |
| e         | jump forward to the end of a word                                     |
| E         | jump forward to the end of a word ( word can contain punctuation )    |
| b         | jump backward to the start of a word                                  |
| B         | jump backward to the start of a word ( word can contain punctuation ) |
| ge        | jump backwards to the end of a word                                   |
| gE        | jump backwards to the end of a word ( word can contain punctuatin )   |
| %         | move cursor to matching character eg: '()' '{}' '[]'                  |
| 0         | jump to the start of the line                                         |
| ^         | jump to the first non-blank character of the line                     |
| $         | jump to the end of the line                                           |
| g_        | jump to the last non-blank character of the line                      |
| gg        | go to the first line of the document                                  |
| G         | go to the last line of the document                                   |
| 5gg or 5G | go to line 5                                                          |
| gd        | move to local declaration                                             |
| gD        | move to global declaration                                            |
| fx        | jump to next occurrence of character x                                |
| tx        | jump to before next occurrence of character x                         |
| Fx        | jump to the previous occurrence of character x                        |
| Tx        | jump to after previous occurrence of character x                      |
| ;         | repeat previous f,t,F or T movement                                   |
| ,         | repeat previous f,t,F or T movement backwards                         |
| }         | jump to next paragraph                                                |
| {         | jump to previous paragraph                                            |
| zz        | center cursor on screen                                               |
| zt        | position cursor on top of the screen                                  |
| zb        | position cursor on bottom of the screen                               |
| ctrl + e  | move screen down one line                                             |
| ctrl + y  | move screen up on line                                                |
| ctrl + b  | move screen up one page                                               |
| ctrl + f  | move screen down one page                                             |
| ctrl + d  | move cursor & screen down 1/2 page                                    |
| ctrl + u  | move cursor & screen up 1/2 page                                      |
 
## INSERT MODE - inserting/appending text
| Command         | Description                                                                |
| --------------- | -------------------------------------------------------------------------- |
| i               | insert before the cursor                                                   |
| I               | insert at the beginning of the line                                        |
| a               | insert (append) after the cursor                                           |
| A               | insert (append) at the end of line                                         |
| o               | append (open) a new line below the current line                            |
| O               | append (open) a new line above the current line                            |
| ea              | insert (append) at the end of the word                                     |
| ctrl + h        | delete the character before the cursor during insert mode                  |
| ctrl + w        | delete word before the cursor during insert mode                           |
| ctrl + j        | add a line break at the cursor position during insert mode                 |
| ctrl + t        | indent (move right) line one shiftwidth during insert mode                 |
| ctrl + d        | de-indent (move left) line one shiftwidth during insert mode               |
| ctrl + n        | insert (auto-complete) next match before the cursor during insert mode     |
| ctrl + p        | insert (auto-complete) previous match before the cursor during insert mode |
| ctrl + rx       | insert the contents of register x                                          |
| ctrl + ox       | Temporarily enter normal mode to issue one normal-mode command x           |
| Esc or ctrl + c | exit insert mode                                                           |

## EDITING
| Command  | Description                                                  |
| -------- | ------------------------------------------------------------ |
| r        | replace a single character                                   |
| R        | replace more than one character, until ~ESC~ is pressed      |
| J        | join line below to the current one with one space in between |
| gJ       | join line below to the current one without space in between  |
| gwip     | reflow paragraph                                             |
| g~       | switch case up to motion                                     |
| gu       | change to lowercase up to motion                             |
| gU       | change to uppercase up to motion                             |
| cc       | change (replace) entire line                                 |
| c$ or C  | change (replace) to the end of the line                      |
| ciw      | change (replace) entire word                                 |
| cw or ce | change (replace) to the end of the word                      |
| s        | delete character and substitute text                         |
| S        | delete line and substitute text                              |
| xp       | transpose two letters (delete and paste)                     |
| u        | undo                                                         |
| U        | restore (undo) last changed line                             |
| ctrl + r | redo                                                         |
| .        | repeat last command                                          |

## MARKING TEXT (Visual mode)
| Command        | Description                                     |
| -------------- | ----------------------------------------------- |
| v              | start visual mode, mark lines, then do  command |
| V              | start linewise visual mode                      |
| o              | move to other end of marked area                |
| ctrl + v       | start visual block mode                         |
| O              | move to other corner of block                   |
| aw             | mark a word                                     |
| ab             | a block with ()                                 |
| aB             | a block with {}                                 |
| at             | a block with <> tags                            |
| ib             | inner block with ()                             |
| iB             | inner block with {}                             |
| it             | inner block with <> tags                        |
| Esc or ctrl +c | exit visual mode                                |

## VISUAL COMMANDS
| Command | Description                     |
| ------- | ------------------------------- |
| >       | shift text right                |
| <       | shift text left                 |
| y       | yank (copy) marked text         |
| d       | delete marked text              |
| ~       | switch case                     |
| u       | change marked text to lowercase |
| U       | change marked text to uppercase |

## REGISTERS
| Command      | Description                              |
| ------------ | ---------------------------------------- |
| :reg[isters] | show registers content                   |
| "xy          | yank into register x                     |
| "xp          | paste contents of register x             |
| "+y          | yank into the system clipboard register  |
| "+p          | paste from the system clipboard register |

## MARKS & POSITIONS
| Command  | Description                                        |
| -------- | -------------------------------------------------- |
| :marks   | list of marks                                      |
| ma       | set current position for mark A                    |
| `a       | jump to position of mark A                         |
| y`a      | yank text to position of mark A                    |
| `0       | go to the position where Vim was previously exited |
| `"       | go to the position when last editing this file     |
| `.       | go to the position of the last change in this file |
| ``       | go to the position before the last jump            |
| :ju[mps] | list of jumps                                      |
| ctrl + i | go to newer position in jump list                  |
| ctrl + o | go to older position in jump list                  |
| :changes | list of changes                                    |
| g,       | go to newer position in change list                |
| g;       | go to older position in change list                |
| ctrl + ] | jump to the tag under cursor                       |

## MACROS
| Command | Description          |
| ------- | -------------------- |
| qa      | record macro a       |
| q       | stop recording macro |
| @a      | run macro a          |
| @@      | rerun last run macro |

## CUT & PASTE
| Command         | Description                                                                                    |
| --------------- | ---------------------------------------------------------------------------------------------- |
| yy              | yank (copy) a line                                                                             |
| 2yy             | yank (copy) 2 lines                                                                            |
| yw              | yank (copy) the characters of the word from the cursor position to the start of the next word  |
| yiw             | yank (copy) word under the cursor                                                              |
| yaw             | yank (copy) word under the cursor and the space after or before it                             |
| y$ or Y         | yank (copy) to end of line                                                                     |
| p               | put (paste) the clipboard after cursor                                                         |
| P               | put (paste) before cursor                                                                      |
| gp              | put (paste) the clipboard after cursor and leave cursor after the new text                     |
| gP              | put (paste) before cursor and leave cursor after the new text                                  |
| dd              | delete (cut) a line                                                                            |
| 2dd             | delete (cut) 2 line                                                                            |
| dw              | delete (cut) the characters of the word from the cursor position to the start of the next word |
| diw             | delete (cut) word under the cursor                                                             |
| daw             | delete (cut) word under the cursor and the space after or before it                            |
| :3,5d           | delete lines starting from 3 to 5                                                              |
| :g/{pattern}/d  | delete all lines containing pattern                                                            |
| :g!/{pattern}/d | delete all lines not containing pattern                                                        |
| d$ or D         | delete (cut) to the end of the line                                                            |
| x               | delete (cut) character                                                                         |

## INDENT TEXT
| Command | Description                                       |
| ------- | ------------------------------------------------- |
| >>      | indent (move right) line one shiftwidth           |
| <<      | de-indent (move left) line one shiftwidth         |
| >%      | indent a block with () or {} (cursor on brace)    |
| <%      | de-indent a block with () or {} (cursor on brace) |
| >ib     | indent inner block with ()                        |
| >at     | indent a block with <> tags                       |
| 3==     | re-indent 3 lines                                 |
| =%      | re-indent a block with () or {} (cursor on brace) |
| =iB     | re-indent inner block with {}                     |
| gg=G    | re-indent entire buffer                           |
| ]p      | paste and adjust indent to current line           |

## SEARCH & REPLACE
| Command        | Description                                                          |
| -------------- | -------------------------------------------------------------------- |
| /pattern       | search for pattern                                                   |
| ?pattern       | search backward for pattern                                          |
| \vpattern      | non-alphanumeric characters are interpreted as special regex symbols |
| n              | repeat search in same direction                                      |
| N              | repeat search in opposite direction                                  |
| :%s/old/new/g  | replace all old with new throughout file                             |
| :%s/old/new/gc | replace all old with new throughout file with confirmation           |
| :noh[lsearch]  | remove highlighting of search matches                                |
| :s/old/new/g   | replace all old with new throughout the line                         |
| :s/old/new/g 5 | replace all old with new in next 5 lines                             |
| :s/old/new     | replace only first match of old with new                             |

## SEARCH IN MULTIPLE FILES
| Command                       | Description                                  |
| ----------------------------- | -------------------------------------------- |
| :vim[grep]/pattern/{`{file}`} | search for pattern in multiple files         |
| :cn[text]                     | jump to the next match                       |
| :cp[revious]                  | jump to the previous match                   |
| :cope[n]                      | open a window containing the list of matches |
| :ccl[ose]                     | close the quickfix window                    |

## TABS
| Command                              | Description                                           |
| ------------------------------------ | ----------------------------------------------------- |
| :tabnew or :tabnew {page.words.file} | open a file in a new tab                              |
| ctrl + wT                            | move the currrent split window into its own tab       |
| gt or :tabn[ext]                     | move to the next tab                                  |
| gT or :tabp[revious]                 | move to the previous tab                              |
| #gt                                  | move to tab number #                                  |
| :tabm[ove] #                         | move current tab to the #th position (indexed from 0) |
| :tabo[nly]                           | close all tabs except for the current one             |
| :tabdo                               | command - run the command on all tabs                 |

## WORKING WITH MULTIPLE FILES
| Command            | Description                                                                      |
| ------------------ | -------------------------------------------------------------------------------- |
| :e[dit] file       | edit a file in a new buffer                                                      |
| :bn[ext]           | go to the next buffer                                                            |
| :bp[revious]       | go to the previous buffer                                                        |
| :bd[delete]        | delete a buffer (close a file)                                                   |
| :b[uffer]#         | go to a buffer by index #                                                        |
| :b[uffer] file     | go to a buffer by file                                                           |
| :ls or :buffers    | list all open buffers                                                            |
| :sp[lit] file      | open a file in new buffer and split window                                       |
| :vs[plit] file     | open a file in a new buffer and vertically split window                          |
| :vert[ical] ba[ll] | edit all buffers and vertical windows                                            |
| :tab ba[ll]        | edit all buffers as tabs                                                         |
| ctrl + ws          | split window                                                                     |
| ctrl + wv          | split window vertically                                                          |
| ctrl + ww          | switch windows                                                                   |
| ctrl + wq          | quit a window                                                                    |
| ctrl + wx          | exchange current window with next one                                            |
| ctrl + w=          | make all windows equal height & width                                            |
| ctrl + wh          | move cursor to the left window (vertical split)                                  |
| ctrl + wl          | move cursor to the right window (vertical split)                                 |
| ctrl + wj          | move cursor to the window below (horizontal split)                               |
| ctrl + wk          | move cursor to the window above (horizontal split)                               |
| ctrl + wH          | make current window full height at far left (leftmost vertical window)           |
| ctrl + wL          | make current window full height at far right (rightmost vertical window)         |
| ctrl + wJ          | make current window full width at the very bottom (bottommost horizontal window) |
| ctrl + wK          | make current window full width at the very top (topmost horizontal window)       |

## Diff
| Command          | Description                                 |
| ---------------- | ------------------------------------------- |
| zf               | manually define a fold up to motion         |
| zd               | delete fold under the cursor                |
| za               | toggle fold under the cursor                |
| zo               | open fold under the cursor                  |
| zc               | close fold under the cursor                 |
| zr               | reduce (open) all folds by one level        |
| zm               | fold more (close) all folds by one level    |
| zi               | toggle folding functionality                |
| ]c               | jump to start of next change                |
| [c               | jump to start on previous change            |
| do or :diffg[et] | obtain (get) difference (from other buffer) |
| dp or :diffpu[t] | put difference (to other buffer)            |
| :diffthis        | make current window part of diff            |
| :dif[fupdate]    | update differences                          |
| :diffo[ff]       | switch off diff mode for current window     |

# Switch Kernels on Arch Linux
+ Check the kernel version by this command
```bash
$ uname -r
```

## Steps to switch kernels
### Step 1: Install the kernel of your choice
There are 4 types of kernel you can choose from.

```bash
$ sudo pacman -S linux

$ sudo pacman -S linux-lts

$ sudo pacman -S linux-hardened

$ sudo pacman -S linux-zen
```

### Step 2: Tweak the grub configuration file to add more kernel options
Follow this two steps
+ Disable grub submenu so that all the available kernel versions are shown on the main screen.
+ Configure grub to recall the last kernel entry you booted and use it as the default entry to boot from the next time.

make change in the grub file
```bash
$ sudo nvim /etc/default/grub
```

add this line of code in the this file
```bash
GRUB_DISABLE_SUBMENU=y
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

+ the first and optional line is used to **disable the GRUB submenu**. 
+ The second line is used to **save the last kernel entry**.
+ last line ensure the GRUB will use as a **default the last saved entry**.

save and exit the configuration file.

### Step 3: Re-generate the GRUB configuration file
To make the change effective you need to re-generate the configuration file.

```bash
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Then the system will reboot

**select the kernel you want in your system.**

![kernel switch](./img/kernelswitch.jpeg)

# xrandr - (manage displays)
Primitive command line interface to RandR extension

Xrandr is used to set the size, orientation and/or reflection of the outputs for a screen. It can also set the screen size.

+ Use the **xrandr** command to list the available displays and their current status. The output will show the name of your connected displays. The display name willl be like **VGA-1**, **HDMI-1** or **DP-1**.
```bash
$ xrandr
```

+ Use the **xrandr --output** command to set up the extended display. Replace **HDMI-1** with the actual name of your display.
```bash
$ xrandr --output HDMI-1 --mode 1920x1080 --pos 0x0 --rotate normal --output <primary-display> --mode 1920x1080 --pos 1920x0 --rotate normal
```

   - --output HDMI-1 : Specifies the output display
   - --mode 1920x1080 : Specifies the resolution of the display.
   - --pos 0x0 : Specifies the position of the display. Adjust the values according to your desired layout.
   - --rotate normal : Specifies the rotation of the display. Use **normal, left, right or inverted** as needed.
   - --output < primary-display > : Specifies the primary display
   - --mode 1920x1080 : Specifies the resolution of the primary display.
   - --pos 1920x0 : Specifies the position of the primary display. Adjust the values based on you desired layout.

+ Set the desired resolution for the second display using the '--mode' option.
```bash
$ xrandr --output HDMI-1 --mode 1920x1080 --right-of <primary-display>
```

   - --output HDMI-1 : Specifies the output display
   - --mode 1920x1080 : Specifies the resolution of the display

+ Specify the resolution for both display.
```bash
$ xrandr --output <primary-display> --mode <primary-resolution> --output HDMI-1 --mode 1920x1080 --right-of <primary-display>
```

   - < primary-display > : Replace with the name of the primary display.
   - < primary-resolution > : Replace with the resolution of your primary display.

+ Duplicate the screen with a **--same-as** 
```bash
$ xrandr --output HDMI-1 --mode 1920x1080 --same-as <primary-display>
```

   - --output HDMI-1 : Specifies the output display
   - --mode 1920x1080 : Specifies the resolution of the display
   - --same-as < primary-display > : Specifies that the display should be duplicated to the primary display.

+ Specify the resolution for both display, using is **--same-as**
```bash
$ xrandr --output <primary-display> --mode <primary-resolution> --output HDMI-1 --mode 1920x1080 --same-as <primary-display>
```

+ Extend the screen with automatic resolution detection
```bash
$ xrandr --output HDMI-1 --auto --right-of <primary-display>
```

   - --auto : Tells xrandr to automatically detect and use the preferred/native resolution of the display.

+ Duplicate the screen with automatic resolution detection.
```bash
$ xrandr --output HDMI-1 --auto --same-as <primary-display>
```

# pacman - (Arch package manager)

## Update the package database:
```bash
$ sudo pacman -Sy
```

+ -S    : Synchronize the package database.
+ -y    : Download a fresh copy of the master package database from the servers.

## Upgrade installed package:
```bash
$ sudo pacman -Syu
```

+ -u    : Upgrade all installed package to their latest version.

## Install a package:
```bash
$ sudo pacman -S <package-name>
```
+ -S    : Install a package.

## Remove a package:
```bash
$ sudo pacman -R <package-name>
```
+ -R    : Remove a package

## Remove a package and it dependencies:
```bash
$ sudo pacman -Rs <package-name>
```
+ -Rs   : Remove a package and its dependencies, if they are not required by other installed package.

## Remove a package, its dependencies and all package that depend on it.
```bash
$ sudo pacman -Rns <package-name>
```
+ -Rns   : Remove a package, its dependencies, and all packages that depend on it.

## Search for a package:
```bash
$ pacman -Ss <search-term>
```

+ -Ss  : Search for a package in the package database.

## Show information about a package:
```bash
$ pacman -Qi <package-name>
```
+ -Qi   : Display detailed information about a package

## List installed package
```bash
$ pacman -Q
```

## List orphaned package
```bash
$ pacman -Qdt
```

## Clean package caches:
```bash
$ sudo pacman -Sc
```

## Clean All Uninstalled package from Cache:
```bash
$ sudo pacman -Scc
```

## List explicity-installed package
```bash
$ pacman -Qe
```

## Identify Orphaned packages:
```bash
$ pacman -Qdtq
```

## Remove Orphaned Packages:
```bash
$ sudo pacman -Rns $(pacman -Qdtq)
```

# pactree - (display tree dependencies)

## Syntax
```bash
$ pactree [option] <package-name>
```

## Display reverse dependencies
```bash
$ pactree -r <package-name>
```

## Display dependencies
```bash
$ pacman <package-name>
```

## example
```bash
$ pactree firefox
```

```bash
$ pactree -r firefox
```

# AUR Helper
## paru
AUR helper and pacman wrapper

### Syntax
```bash
$ paru <operation> [options] [targets]

$ paru <search terms>

$ paru
```

+ Search for Packages:
```bash
$ paru -Ss package-name
```

+ Install a package from AUR:
```bash
$ paru -S package-name
```

+ Remove a Package intalled from AUR:
```bash
$ paru -R package-name
```

+ Upgrade AUR packages:
```bash
$ paru -Syu
```

+ Update Package information:
```bash
$ paru -Sy
```

+ List installed AUR package:
```bash
$ paru -Q
```

+ Show information about a package:
```bash
$ paru -Si package-name
```

+ check for AUR Pacakge Update:
```bash
$ paru -Qua
```

+ Clean up orphaned packages:
```bash
$ paru -Rns $(paru -Qdtq)
```

+ install AUR Package Without Confirmation:
```bash
$ paru -S --noconfirm package-name
```

+ Remove Unneeded Dependencies:
```bash
$ paru -Rns $(paru -Qdtq)
```

+ Update **paru** itself:
```bash
$ paru -S paru
```

## yay
AUR helper written in go

### Syntax
```bash
$ yay <operation> [option] [targets]

$ yay <search terms>

$ yay
```

+ Search for package:
```bash
$ yay -Ss package-name
```

+ Install a package from AUR:
```bash
$ yay -S package-name
```

+ Remove a Package Installed from AUR:
```bash
$ yay -R package-name
```

+ Upgrade AUR package:
```bash
$ yay -Syu
```

+ Update Package Information:
```bash
$ yay -Sy
```

+ List intalled AUR Package:
```bash
$ yay -Q
```

+ Show information about a Package:
```bash
$ yay -Si package-name
```

+ Check for AUR Package Updates:
```bash
$ yay -Qua
```

+ Clean up orphaned packages:
```bash
$ yay -Rns $(yay -Qdtq)
```

+ Install AUR package without Confirmation:
```bash
$ yay -S --noconfirm package-name
```

+ Remove Unneeded Dependencies:
```bash
$ yay -Rns $(yay -Qdtq)
```

+ Update **yay** itself:
```bash
$ yay -S yay
```

# Apache Service
httpd - Apache Hypertext Transfer Protocol Server

+ Install Apache:
```bash
$ sudo pacman -S apache
```

+ Start Apache
```bash
$ sudo systemctl start httpd
```

+ Stop Apache:
```bash
$ sudo systemctl stop httpd
```

+ Restart Apache:
```bash
$ sudo systemctl restart httpd
```

+ Enable Apache to start on boot:
```bash
$ sudo systemctl enable httpd
```

+ Disable Apache from starting on boot:
```bash
$ sudo systemctl disable httpd
```

+ Check Apache status:
```bash
$ sudo systemctl status httpd
```

+ Reload Apache configuration without restarting:
```bash
$ sudo systemctl reload httpd
```

+ Test Apache configuration for syntax errors:
```bash
$ sudo apachectl configtest
```

+ Open the Apache configuration file in a text editor
```bash
$ sudo nvim /etc/httpd/conf/httpd.conf
```

# Enable SSH
OpenSSH daemon

+ Install OpenSSH:
```bash
$ sudo pacman -S openssh
```

+ Start the SSH service:
```bash
$ sudo systemctl start sshd
```

+ Enable SSH to start on boot:
```bash
$ sudo systemctl enable sshd
```

+ Check the status of the SSH service:
```bash
$ sudo systemctl status sshd
```

# Auto Mount Drives in Linux on Boot
## Step1:
Make a directory with the name Backup in a /media directory.
```bash
$ sudo mkdir /media/Backup
```

## Step2: 
Then collect the information of disk which you want to mount.

+ To find the mounted path of the disk e.g. /dev/sdb1
```bash
$ sudo fdisk -l
```

+ To collect the UUID information of disk
```bash
$ sudo blkid
```

## Step3: 
Edit the fstab folder, and it is very sensitive.
```bash
$ sudo vim /etc/fstab
```

+ Edit the file and add the information you collected in this file.

## Step4:
At the end the file should look like this.
![fstab](./img/fstab.png)

## Step5:
to make shore the mount is proper run this command, this command will mount the disk form the fstab folder.
```bash
$ sudo mount -a
```


