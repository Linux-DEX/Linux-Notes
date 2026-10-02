# Install tor or tor-browser
```bash
$ sudo pacman -S tor

$ sudo pacman -S tor-browser
```

# Install proxychains
```bash
$ sudo pacman -S proxychains-ng
```

# Tor services

+ To check the tor service
```bash
$ sudo systemctl status tor
```

+ To start the tor service
```bash
$ sudo systemctl start tor
```

+ To stop the tor service
```bash
$ sudo systemctl stop tor
```

# Running the firefox with the tor network

+ **STEP-1** : Start the tor service
```bash
$ sudo systemctl start tor
```

+ **STEP-2**: Run the firefox with the proxychain
```bash
$ proxychains firefox
```

> [!TIP]
> *If you don't want to run tor with firefox directly run tor-browser.*














