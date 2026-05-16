
# update
```
sudo apt update && sudo apt upgrade -y
```

```
sudo apt update && sudo apt full-upgrade -y
```

```
sudo apt autoremove -y
```

## fixes
```
sudo apt full-upgrade -y
sudo apt install libgnuradio-qtgui3.10.12 spike
sudo apt full-upgrade -y
sudo apt install libqt5core5t64=5.15.17+dfsg-7+b1
sudo apt autoremove -y && sudo apt clean
```
# ssh rdp
```
sudo apt update && sudo apt install -y openssh-server xrdp kali-desktop-xfce && sudo systemctl enable --now ssh xrdp
```

# pimpmy kali

```
git clone https://github.com/Dewalt-arch/pimpmykali.git ~/tools/pimpmykali && cd ~/tools/pimpmykali && sudo ./pimpmykali.sh --newvm && cd ~ && rm -rf ~/tools/pimpmykali
```
This:
1. Clones the repo
2. Runs the automated new VM setup
3. Returns to your home directory
4. Deletes the pimpmykali folder afterward
# Comfort Tools

rlwrap and penelope
```
sudo apt update && sudo apt install -y python3 python3-pip rlwrap && python3 -m pip install penelope-shell
```

```
sudo apt update && sudo apt install -y pipx && pipx ensurepath && pipx install git+https://github.com/brightio/penelope
```

Obsidian
```
wget -O /tmp/obsidian.deb "$(curl -s https://api.github.com/repos/obsidianmd/obsidian-releases/releases/latest | grep browser_download_url | grep amd64.deb | cut -d '"' -f 4)" && sudo apt install -y /tmp/obsidian.deb
```