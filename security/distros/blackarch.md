# What is BlackArch Linux?

BlackArch is a complete linux distribution for penetration testers and security researchers. It is derived from **ArchLinux** and users can install BlackArch components individually or in groups directly on top of it.

# Installing on top of ArchLinux

## Method 1

1. **Add the BlackArch Repository:**
Open the **/etc/pacman.conf** file in a text editor.
```bash
$ sudo vim /etc/pacman.conf
```

+ Add the following lines at the end of the file:
```bash
[blackarch]
SigLevel = Optional TrustAll
Server = https://blackarch.org/blackarch/$repo/os/$arch
```

*Save the changes and exit the text editor.*

2. **Import the BlackArch Keyring:**
You need to import the BlackArch  keyring to verify the integrity of package from the BlackArch repository. Run the following commands.
```bash
$ sudo pacman -Syy
$ sudo pacman -S blackarch-keyring
```

3. **Update Pacman Database:**
After adding the BlackArch repository and importing the keyring, update your Pacman database.
```bash
$ sudo pacman -Sy
```

4. **Install BlackArch Packages:**
Now you can install Blackarch packages using Pacman. For example, to intall a package called **blackarch-package-name**, you can use:
```bash
$ sudo pacman -S blackarch-package-name
```

## Method 2

1. **Download BlackArch script**
```bash
$ curl -O https://blackarch.org/strap.sh
```

2. **Verify the SHA1 sum**
```bash
$ echo 5ea40d49ecd14c2e024deecf90605426db97ea0c strap.sh | sha1sum -c
```

3. **Set execute bit**
```bash
$ chmod +x strap.sh
```

4. **Run strap.sh**
```bash
$ sudo ./strap.sh
```

5. **Update the repositories or update the system**
```bash
$ sudo pacman -Syu
```

# Installing tools from BlackArch

+ **To List all of the available tools, run**
```bash
$ sudo pacman -Sgg | grep blackarch | cut -d' ' -f2 | sort -u
```

+ **To intall all of the tools, run**
```bash
$ pacman -S blackarch
```

+ **To install a category of tools, run**
```bash
$ sudo pacman -S blackarch-<category>
```

+ **To see the blackarch categories, run**
```bash
$ sudo pacman -Sg | grep blackarch
```

+ **To search for a specific package, run**
```bash
$ pacman -Ss <package-name>
```

+ **It may be necessary to overwrite certain package when installing blackarch tools. If you experience "failed to commit transaction" errors, use the --needed and --overwrite switches**
```bash
$ sudo pacman -Syyu --needed --overwrite='*' <wanted-package>
```

# Installing package from source

As part of an alternative method of installation, you can build the BlackArch package from source. To build the entire repo, you can use the =Blackman= tool.

+ **First, you have to install Blackman. If the BlackArch package repository is setup on you machine, you can install Blackman.**
```bash
$ pacman -S blackman
```

+ **you can build and install Blackman from source:**
```bash
$ mkdir blackman
$ cd blackman
$ wget https://raw2.github.com/BlackArch/blackarch/master/packages/blackman/PKGBUILD
$ makepkg -s
```
#+end_example

+ **Or you can install Blackman from the AUR:**
```bash
$ <AUR helper> -S blackman
```

# Basic Blackman usage

+ **Download, compile and install package:**
```bash
$ sudo blackman -i package
```

+ **Download, compile and install whole category:**
```bash
$ sudo blackman -g group
```
 
+ **Download, compile and install all of the BlackArch tools:**
```bash
$ sudo blackman -a
```

+ **To list the blackarch categories:**
```bash
$ blackman -l
```

+ **To list category tools:**
```bash
$ blackman -p category
```

+ **To update all installed BlackArch tools to their latest version, use teh '-u' option:**
```bash
$ sudo blackman -u
```

+ **To remove a package installed from the Blackarch repository, use the '-r' option followed by the package name:**
```bash
$ sudo blackman -r package-name
```

+ **To synchronize the BlackArch package database and update it, you can use the '-Syy' option:**
```bash
$ sudo blackman -Syy
```

+ **To search for a package in the BlackArch repository, you can use the *blackman* command with the '-Ss' option:**
```bash
$ sudo blackman -Ss package-name
```







































