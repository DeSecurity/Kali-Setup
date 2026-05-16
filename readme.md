# Kali Linux Initial Setup (OSCP / Labs) 

This README is a **first-boot checklist and reference** for setting up a fresh Kali Linux VM for OSCP-style labs and general pentesting.

Philosophy:

* Minimize manual clicks.
* Install everything once.
* Cache what you need offline.
* Keep tooling predictable.

This guide is organized **top-down in execution order**.

---
## 0. Assumptions

* Kali Linux **kali-linux-default** desktop image
* You have sudo access
* Internet access is available during setup
* You will later replace parts of this with custom scripts
---
## 1. One-Liner: Full Base Setup (Fast Path)

Upstream (non-Kali) tools:

```bash
# Kerbrute
wget -O kerbrute https://github.com/ropnop/kerbrute/releases/download/v1.0.3/kerbrute_linux_amd64 && \
chmod +x kerbrute && sudo mv kerbrute /usr/local/bin/

# Katana
go install github.com/projectdiscovery/katana/cmd/katana@latest && \
sudo cp ~/go/bin/katana /usr/local/bin/katana

# Dalfox
go install github.com/hahwul/dalfox/v2@latest && \
sudo cp ~/go/bin/dalfox /usr/local/bin/dalfox
```

---

## 2. Pimp My Kali (Temporary Bootstrap)

This is a **temporary convenience layer** until custom scripts replace it.

### Install

```bash
git clone https://github.com/Dewalt-arch/pimpmykali.git ~/tools/pimpmykali
cd ~/tools/pimpmykali
sudo ./pimpmykali.sh
```

### Recommended Options

* System update and upgrade
* Core pentesting tools
* Wordlists and extra utilities
* Shell quality-of-life improvements

Avoid:

* Heavy desktop theming
* Niche tools you do not recognize

Goal is **baseline parity**, not bloat.

---

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

---
### Kerbrute

```bash
kerbrute userenum -d domain.local --dc 10.10.10.10 users.txt
```

---
### Katana

```bash
katana -u https://target.tld -silent
```

---
### Dalfo

```bash
dalfox url "https://target/page.php?x=1"
```

---

## 8. Optional: Nessus (Install Only If Required)

Do **not** include Nessus in one-liners.

High-level steps:

1. Download Nessus .deb from Tenable
2. Install

   ```bash
   sudo dpkg -i Nessus-*.deb
   sudo systemctl start nessusd
   ```
3. Browse to `https://localhost:8834`
4. Activate (Essentials or licensed)
5. Create local user

Only install if:

* Lab explicitly allows it
* Time cost is justified

---

## 9. Final Notes

* Snapshot the VM after completion
* Keep tooling minimal during exams
* Prefer manual exploitation over automation

This README is a **living document**. Replace sections with scripts as automation matures.

add, install remmina,
addworkflow remina to copy and paste cleanly to desktop enviro
ssh to copy and past cmds
