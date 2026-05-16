Install CIFS support:

```
sudo apt update && sudo apt install -y cifs-utils
```

Create a mount point:

```
sudo mkdir -p /mnt/windows-share
```

Create a credentials file:

```
sudo nano /etc/samba/windows-share.creds
```

Put this inside:

```
username=YOUR_WINDOWS_USERNAMEpassword=YOUR_WINDOWS_PASSWORDdomain=WORKGROUP
```

Secure it:

```
sudo chmod 600 /etc/samba/windows-share.creds
```

Test the mount manually first:

```
sudo mount -t cifs //172.16.15.12/KaliShare /mnt/windows-share -o credentials=/etc/samba/windows-share.creds,uid=$(id -u),gid=$(id -g)
```

If that works, make it persistent:

```
sudo nano /etc/fstab
```

Add this line:

```
//172.16.15.12/KaliShare /mnt/windows-share cifs credentials=/etc/samba/windows-share.creds,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,iocharset=utf8,nofail,x-systemd.automount,_netdev 0 0
```

Test without rebooting:

```
sudo umount /mnt/windows-share
sudo systemctl daemon-reload
sudo mount -a
```

Then verify:

```
df -h | grep windows-share
```

Now it will auto-mount across reboots.

test
```
ls -la /mnt/windows-share
touch /mnt/windows-share/test-from-kali.txt
```