
## 3. Browser Setup (Firefox ESR)

### Install Burp CA Certificate

1. Start Burp
2. Proxy tab → Open browser (or manual Firefox)
3. Visit `http://burp`
4. Download CA certificate
5. Firefox Settings → Privacy & Security → Certificates → Import
6. Trust for identifying websites

### Required Add-ons

Install from Firefox Add-ons:

* **FoxyProxy Standard**
* **Wappalyzer**
* **Hack-Tools**

### FoxyProxy

* Create profile: `Burp`
* Proxy: `127.0.0.1:8080`
* Default mode: Disabled
* Toggle only when testing

### Import Bookmarks

```bash
git clone https://github.com/YOUR_GITHUB/bookmarks.git ~/bookmarks
```

Firefox → Bookmarks → Manage → Import HTML → select file

---

## 4. Burp Suite Setup

* Disable auto-updates (lab stability)
* Set temporary project directory
* Enable Logger
* Set scope aggressively

Optional:

* Install extensions only if needed


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

remember to change root terminal as well

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
Virtual machine management settings,

consider creating a shared folder for the vms to access because sometime there are issue with copy pasting etc between the host and kali machine, 