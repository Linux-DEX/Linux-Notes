# Features
+ Obtain device information without any permission!
+ Access Location **SMARTPHONE**
+ Access webcam
+ Access Microphone

# Software Installation
## Install Storm-Breaker
1. Clone git repo
```bash
$ cd /opt

$ git clone https://github.com/ultrasecurity/Storm-Breaker.git
```

2. Move to Storm-Breaker directory
```bash
$ cd Storm-Breaker/
```

3. Run the install.sh script
```bash
$ bash install.sh
```

4. To run the Strom-Breaker
```bash
$ python3 st.py
```

## Install ngrok
1. Download ngrok 

[ngrok-download](https://ngrok.com/download)

2. extract the file using tar command
```bash
$ sudo tar -xvzf ~/Downloads/ngrok-v3-stable-linux-amd64.tgz -C /usr/local/bin
```

3. Create an account in ngrok site.

4. after login, than connect you account using the token given in ngrok account website.
```bash
$ ngrok config add-authtoken <token>
```
- run this command on the terminal.

# Start
## run Storm-Breaker
+ move to the Storm-Breaker file and run this command
```bash
$ python3 st.py
```

![storm-breaker](./img/storm-breaker.png)

## to run ngrok
```bash
$ ngrok http 2525
```

## Open the ngrok link
 Open the link given in the **forwarding** session 

### login the site
![storm break login](./img/storm-break-login.png)

### Default username and password
+ `username` : `admin`
+ `password` : `admin`

## Other links and main contain

![storm breaker ngrok](./img/storm-breaker-ngrok.png)

+ All the link specified here can be shared to other user for specified target.
+ The contant will be visible in result box.
+ other option stop/start , download logs, and clear logs are avialable.