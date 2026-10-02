# Changing adapter to monitor mode

```bash
$ sudo ifconfig wlp3s0 down

$ sudo iwconfig wlp3s0 mode monitor
```

# Changing adapter to managed

```bash
$ sudo ifconfig wlp3s0 down

$ sudo iwconfig wlp3s0 mode managed

$ sudo systemctl restart NetworkManager
```

# Using iw command

1. **Check Current Mode:**
```bash
$ iw dev [interface_name] info
```

2. **Change interface Mode:**
```bash
$ sudo iw dev [interface_name] set type [new_mode]
```

- example
```bash
$ sudo iw dev wlp3s0 set type monitor
```

3. **Verify Mode Change:**
```bash
$ iw dev wlp3s0 info
```

+ **To up the interface:**
```bash
$ sudo ifconfig wlp3s0 up 
```

































