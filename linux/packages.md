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

A config you have edited is not overwritten. Pacman leaves a `.pacnew` beside it. Merging those files is `linux/pacnew.md`.

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

