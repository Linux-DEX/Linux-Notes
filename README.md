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
| [tmux](linux/tmux.md) | sessions, windows, panes |
| [Docker](linux/docker.md) | images, containers, build, volumes, compose |
| [Kubernetes](linux/kubernetes.md) | kubectl, Helm, minikube, kind, k9s |
| [cron](linux/cron.md) | cronie and crontab |
| [ffmpeg](linux/ffmpeg.md) | inspect and convert media |
| [sqlite](linux/sqlite.md) | one-file SQL database |
| [iotop](linux/iotop.md) | disk I/O by process |
| [Syncthing](linux/syncthing.md) | folder sync between your machines |
| [Git](linux/git.md) | status, commit, branch, push |
| [lazygit](linux/lazygit.md) | terminal UI for a Git repo |
| [GitHub CLI](linux/gh.md) | `gh` login, pull requests, issues |
| [tldr](linux/tldr.md) | short example pages for commands |
| [ShellCheck](linux/shellcheck.md) | find bugs in a shell script |
| [HTTPie](linux/httpie.md) | HTTP requests from the terminal |
| [ImageMagick](linux/imagemagick.md) | identify, resize, convert images |
| [strace](linux/strace.md) | system calls of a process |
| [fwupd](linux/fwupd.md) | device firmware updates |
| [keyd](linux/keyd.md) | Wayland key remapping |
| [Password manager](linux/password-manager.md) | GnuPG and `pass` |

## Security tools

Original command notes, sorted by what the tool is for.

| Area | Notes |
| ---- | ----- |
| Auditing | [Lynis](security/auditing/lynis.md), [arch-audit](security/auditing/arch-audit.md), [ssh-audit](security/auditing/ssh-audit.md), [sslscan](security/auditing/sslscan.md), [openssl](security/auditing/openssl.md), [ClamAV](security/auditing/clamav.md), [fail2ban](security/auditing/fail2ban.md), [firejail](security/auditing/firejail.md), [systemd-analyze](security/auditing/systemd-analyze.md), [AIDE](security/auditing/aide.md), [auditd](security/auditing/auditd.md), [rkhunter](security/auditing/rkhunter.md), [unhide](security/auditing/unhide.md), [USBGuard](security/auditing/usbguard.md), [OpenSnitch](security/auditing/opensnitch.md), [osquery](security/auditing/osquery.md), [checksec](security/auditing/checksec.md), [Trivy](security/auditing/trivy.md), [syft](security/auditing/syft.md), [gitleaks](security/auditing/gitleaks.md), [cosign](security/auditing/cosign.md) |
| Distro | [BlackArch](security/distros/blackarch.md) |
| Network | [nmap](security/network/nmap.md), [tcpdump](security/network/tcpdump.md), [Wireshark](security/network/wireshark.md), [nethogs](security/network/nethogs.md), [mtr](security/network/mtr.md), [whois](security/network/whois.md), [netcat](security/network/netcat.md), [arp](security/network/arp.md), [netdiscover](security/network/netdiscover.md), [adapter mode](security/network/network-adapter.md) |
| Web | [Nikto](security/web/nikto.md), [WhatWeb](security/web/whatweb.md), [gobuster](security/web/gobuster.md), [DirBuster](security/web/dirbuster.md), [Skipfish](security/web/skipfish.md), [WebKiller](security/web/webkiller.md) |
| Wireless | [Aircrack-ng](security/wireless/aircrack-ng.md), [Wifite](security/wireless/wifite.md), [Fluxion](security/wireless/fluxion.md) |
| Passwords | [KeePassXC](security/passwords/keepassxc.md), [pwgen](security/passwords/pwgen.md), [John the Ripper](security/passwords/john-the-ripper.md), [Hydra](security/passwords/hydra.md) |
| Frameworks | [Metasploit](security/frameworks/metasploit.md) |
| OSINT | [Sherlock](security/osint/sherlock.md) |
| Social engineering | [Seeker](security/social-engineering/seeker.md), [Storm-Breaker](security/social-engineering/storm-breaker.md) |
| Privacy | [Tor](security/privacy/tor.md), [dnscrypt-proxy](security/privacy/dnscrypt-proxy.md), [WireGuard](security/privacy/wireguard.md), [uBlock Origin](security/privacy/ublock-origin.md), [BleachBit](security/privacy/bleachbit.md), [mat2](security/privacy/mat2.md), [age](security/privacy/age.md), [GnuPG](security/privacy/gpg.md) |
| Steganography | [steghide](security/steganography/steghide.md) |

## Reference

| Note | What is in it |
| ---- | ------------- |
| [Markdown](reference/markdown.md) | Markdown cheat sheet |
| [Org mode](reference/org-mode.md) | Emacs Org cheat sheet |
