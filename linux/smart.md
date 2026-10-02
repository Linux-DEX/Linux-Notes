# Drive health

`smartctl` reads the drive's own health log. Install `smartmontools`.

```bash
$ sudo pacman -S smartmontools
$ sudo smartctl -H /dev/sda
$ sudo smartctl -a /dev/sda
```

A SATA disk is `/dev/sda`. An NVMe drive is the controller, `/dev/nvme0`, not the namespace `/dev/nvme0n1`.

`-H` is the pass or fail line. `-a` is the full log. On a SATA disk, a rising `Reallocated_Sector_Ct` or any `Current_Pending_Sector` means the disk is failing. On NVMe, read `Percentage Used`, `Available Spare`, and `Media and Data Integrity Errors`. Copy the data off before the drive stops answering.

## Short test

```bash
$ sudo smartctl -t short /dev/sda
```

The command prints how many minutes the test takes. It runs on the drive while you keep using the machine. Read the result afterward with `smartctl -a`. The self-test log is at the bottom.

## Watch it

`smartd` checks the drives in the background and logs failures.

```bash
$ sudo systemctl enable --now smartd
```
