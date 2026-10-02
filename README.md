# Linux Notes

Arch-focused notes. Linux administration is under `linux/`. Tool notes are under `security/`, grouped by job. Screenshots are in `assets/images/`.

## Linux

| Note | What is in it |
| ---- | ------------- |
| [Filesystem](linux/filesystem.md) | Directory tree, ext4 / XFS / Btrfs / swap, mounting, fstab |
| [Kernel and boot](linux/kernel-and-boot.md) | Kernel flavors, GRUB, systemd-boot, switching kernels on Arch |
| [systemd](linux/systemd.md) | Units, systemctl, the journal, timers |
| [Users and groups](linux/users-and-groups.md) | Accounts, sudo, wheel, umask |
| [Packages](linux/packages.md) | pacman, pactree, paru, yay |
| [pacnew](linux/pacnew.md) | `.pacnew`, `.pacsave`, `pacdiff` |
| [Mirrors](linux/mirrors.md) | reflector |
| [mkinitcpio](linux/mkinitcpio.md) | initramfs, presets, rebuild |
| [LUKS](linux/luks.md) | unlock a data disk, crypttab |
| [SMART](linux/smart.md) | `smartctl`, `smartd` |
| [Backups](linux/backups.md) | restic on `/media/Backup` |
| [Troubleshooting](linux/troubleshooting.md) | full disk, emergency shell, previous boot |
| [Services](linux/services.md) | httpd, sshd, SSH client, scp, rsync |
| [Firewall](linux/firewall.md) | nftables, ufw |
| [Networking](linux/networking.md) | NetworkManager, Bluetooth, address, DNS |
| [Display](linux/display.md) | X11, Wayland, xrandr |
| [Commands](linux/commands.md) | Command reference |
| [Vim](linux/vim.md) | Vim and Neovim keys |
| [File managers](linux/file-managers.md) | ranger |
| [Shell](linux/shell.md) | `chsh`, bash, fish |
| [Git](linux/git.md) | status, commit, branch, push |
| [keyd](linux/keyd.md) | Wayland key remapping |
| [Password manager](linux/password-manager.md) | GnuPG and `pass` |

## Security tools

Original command notes, sorted by what the tool is for.

| Area | Notes |
| ---- | ----- |
| Auditing | [Lynis](security/auditing/lynis.md), [arch-audit](security/auditing/arch-audit.md), [ssh-audit](security/auditing/ssh-audit.md), [ClamAV](security/auditing/clamav.md), [fail2ban](security/auditing/fail2ban.md), [firejail](security/auditing/firejail.md) |
| Distro | [BlackArch](security/distros/blackarch.md) |
| Network | [nmap](security/network/nmap.md), [tcpdump](security/network/tcpdump.md), [netcat](security/network/netcat.md), [arp](security/network/arp.md), [netdiscover](security/network/netdiscover.md), [adapter mode](security/network/network-adapter.md) |
| Web | [Nikto](security/web/nikto.md), [WhatWeb](security/web/whatweb.md), [gobuster](security/web/gobuster.md), [DirBuster](security/web/dirbuster.md), [Skipfish](security/web/skipfish.md), [WebKiller](security/web/webkiller.md) |
| Wireless | [Aircrack-ng](security/wireless/aircrack-ng.md), [Wifite](security/wireless/wifite.md), [Fluxion](security/wireless/fluxion.md) |
| Passwords | [John the Ripper](security/passwords/john-the-ripper.md), [Hydra](security/passwords/hydra.md) |
| Frameworks | [Metasploit](security/frameworks/metasploit.md) |
| OSINT | [Sherlock](security/osint/sherlock.md) |
| Social engineering | [Seeker](security/social-engineering/seeker.md), [Storm-Breaker](security/social-engineering/storm-breaker.md) |
| Privacy | [Tor](security/privacy/tor.md) |
| Steganography | [steghide](security/steganography/steghide.md) |

## Reference

| Note | What is in it |
| ---- | ------------- |
| [Markdown](reference/markdown.md) | Markdown cheat sheet |
| [Org mode](reference/org-mode.md) | Emacs Org cheat sheet |
