# Introduction
+ Concept behind Seeker is simple, just like we `host phishing page` to get credentials why not host a fake page that requests your location like many popular location based websites.
+ *Seeker Hosts a fake website which asks for location Permission* and if the target allows it, we get:
    - Longitude
    - Latitude
    - Accuracy
    - Altitude - not always available
    - Direction - Only available if user is moving
    - Speed - Only available if user is moving
+ Along with location information we also get **Device Information** without any permissions:
    - Unique ID using Canvas FingerPrinting
    - Device Model - not always available
    - Operating system
    - Platform
    - Number of CPU Cores - Approximate Results
    - Amount of RAM - Approximate Results
    - Screen Resolution
    - GPU Informaton
    - Browser Name and Version
    - Public IP Address
    - Local IP Address
    - Local Port      

# Installation
## Install from github
```bash
$ git clone https://github.com/thewhiteh4t/seeker.git
$ cd seeker/
$ chmod +x install.sh
$ ./install.sh
```

## Install on BlackArch
```bash
$ sudo pacman -S seeker
or
$ blackman -i seeker
```

# Usage
## Help page
```bash
$ python3 seeker.py -h
```

+ on BlackArch
```bash
$ sudo seeker -h
```

## Syntax
```bash
$ seeker.py [-h] [-k KML] [-p PORT] [-u] [-v] [-t TEMPLATE] [-d] [--telegram token:chatId] [--webhook WEBHOOK]
```

## Options:
+  -h, --help                           : show this help message and exit
+  -k KML, --kml KML                    : KML filename
+  -p PORT, --port PORT                 : Web server port [ Default : 8080 ]
+  -u, --update                         : Check for updates
+  -v, --version                        : Prints version
+  -t TEMPLATE, --template TEMPLATE     : Auto choose the template with the given index
+  -d, --debugHTTP                      : Disable auto http --> https redirection for testing purposes 
                                         (only works for the templates having index_temp.html file)
+  --telegram                           : Send info to a telegram bot, provide telegram token and chat to use
                                         format = token:chatId separated by a colon
+  --webhook                            : Send events to a webhook endpoint to be processed

> [!NOTE]
> Note : endpoint must be unauthenticated and accept POST request

### Variables:
+ DEBUG_HTTP            : Same as -d, --debugHTTP
+  PORT                        : Same as -p, --port
+  TEMPLATE                : Same as -t, --template
+  TITLE                        : Provide the group title or the page title
+  REDIRECT                 : Provide the URL to redirect the user to, after the job is done
+  IMAGE                      : Provide the image to use, can either be remote (http or https) or local
                            Note : Remote image will be downloaded locally during the startup
+  DESC                         : Provide the description of the item (group or webpage depending on the template)
+  SITENAME                 : Provide the name of the website
+  DISPLAY_URL             : Provide the URL to display on the page
+  MEM_NUM                : Provide the number of group membres (Telegram so far)
+  ONLINE_NUM            : Provide the number of the group online members (Telegram so far)
+  TELEGRAM                 : Provide telegram token and chat to use to send info to a telegram bot
                            format = token:chatId separated by a colon
+  WEBHOOK                  : Provide the webhook url to forward the events to 
                            Note : endpoint should be unauthenticated and accept POST method
                            

## Example

1. In first terminal.
```bash
$ python3 seeker.py
or
$ sudo seeker
```

2. In second terminal start a tunnel service such as ngrok
```bash
$ ./ngrok http 8080
```

+ Open KML file for Google Earth
```bash
$ python3 seeker.py -k <filename>
```

+ Use custom port
```bash
$ python3 seeker.py -p 1337
$ ./ngrok http 1337
```

+ Pre-select a specific template
```bash
$ python3 seeker.py -t 1
```

> [!REFERENCE]
> [github seeker tool](https://github.com/thewhiteh4t/seeker)


