update
```
sudo apt update -y && sudo apt upgrade -y
```

`Take Snapshot 1`

---
Change power manager settings
system suspend never

display never

screen saver 0 off

add root terminal to desktop - this saves time 

---
Change terminal settings

`Appearance Tab`
increase terminal font to 20
color scheme changed to linux
checkbox draw a border

---

install addons 

foxyproxy
https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/
make a profile for burp
add profile 
title:burp
hostname:127.0.0.1
port:8080

install burp cert
http://burp/cert
firefox
settings> privacy & security > view certificates > authorities > import

wappalyzer
https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/

builtwith
https://addons.mozilla.org/en-US/firefox/addon/builtwith/

hack-tools
https://addons.mozilla.org/en-US/firefox/addon/hacktools/

dark reader
https://addons.mozilla.org/en-US/firefox/addon/darkreader/

---
setup burp suite

start burp suite
settings > user interface > display > dark
font size > 14

---

setup bookmarks

---
install tools
mkdir -p /opt/tools/privesc
mkdir -p /opt/tools/webshells
mkdir -p /opt/tools/pivoting

wget 
linpeas
winpeas


apt install seclists -y

gzip -d /usr/share/wordlists/rockyou.txt

consider installing gedit

---
usefull paths
/usr/share/windows-binaries


usefull commands 
in terminal

CTRL + SHFIT + R 
splits the terminal down the midlle

CTRL + SHFIT + D
splits  across the middle left to right

CTRL + d 
deletes last split

CTRL + t
new terminal tab

---
Virtual machine management settings,

consider creating a shared folder for the vms to access because sometime there are issue with copy pasting etc between the host and kali machine, 

ensure copy and paste is set to bidirectional

---
take a snapshot 2

stuff to add to install

nxcspray,
booodhound docker container,

### 1) Install Docker on Kali

A simple Kali-compatible route is:

```
sudo apt update
sudo apt install -y docker.io docker-compose-v2 wget tarsudo systemctl enable --now docker
sudo usermod -aG docker $USERnewgrp docker
```

SpecterOps requires Docker for CE, though their docs reference Docker Desktop generically.

### 2) Download the latest BloodHound CLI

For amd64 Kali:

```
wget https://github.com/SpecterOps/bloodhound-cli/releases/latest/download/bloodhound-cli-linux-amd64.tar.gz
```

That is the official documented Linux download URL.

If your Kali is ARM, use the matching ARM release from the same BloodHound CLI releases page. SpecterOps notes you should pick the binary for your architecture.

### 3) Extract it

```
tar -xvzf bloodhound-cli-linux-amd64.tar.gz
chmod +x bloodhound-cli
```

The `tar -xvzf` step is in the official quickstart.

### 4) Install BloodHound CE

```
./bloodhound-cli install
```

This is the documented install command.

### 5) Save the generated admin password

When setup finishes, the CLI prints a randomly generated password for the `admin` account. SpecterOps explicitly tells you to keep that password.

### 6) Open the UI

Browse to:

```
http://localhost:8080/ui/login
```

Log in with:

```
username: adminpassword: <generated password from install>
```

Then change the password when prompted.

### 7) If you lose the password

Run:

```
./bloodhound-cli resetpwd
```

That is the official reset command.

```
sudo apt update  
sudo apt install -y docker.io docker-compose
```


Your BloodHound stack path is:

```
/root/.config/bloodhound
```

## Bring stack down

```
sudo sucd /root/.config/bloodhounddocker compose down
```

## Bring stack up

```
sudo sucd /root/.config/bloodhounddocker compose up -d
```

## Check status

```
docker ps
```

## Open BloodHound

```
http://localhost:8080/ui/login
```

## One-line commands from anywhere

Down:

```
sudo docker compose -f /root/.config/bloodhound/docker-compose.yml down
```

Up:

```
sudo docker compose -f /root/.config/bloodhound/docker-compose.yml up -d
```
# Binaries to install

## Linux
nxcspray,
ligolo-ng proxy

## Windows

Ligolo-ng agent,
get linux proxy, and windows/linux agent,

Daniels Github Binaries
