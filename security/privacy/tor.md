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

# Which Tor to use

`tor-browser` is a browser built to use Tor. It has its own Tor process. You do not need the `tor` service running, and you do not need proxychains.

`proxychains firefox` only redirects some of Firefox's connections. DNS and WebRTC can still leave outside Tor, so the browser is identifiable as a normal Firefox. Use Tor Browser for browsing.

The `tor` service is a local SOCKS proxy on `127.0.0.1:9050`. Leave it for a program that is written to use a SOCKS proxy. Do not open that port on a LAN address. The default config already binds it to localhost.

Tor Browser shows the circuit it is using. If the browser cannot connect, the system `tor` service is not the thing to debug. They are separate.














