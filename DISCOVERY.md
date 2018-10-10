## Nmap

```bash
# Identify target addresses on network
nmap -sn 10.11.1.1/24

# Scan default 1000 ports
nmap 10.11.1.22

# Scan for service version, default scripts and OS version
nmap -sV -sC -O 10.11.1.22

# Scan all 65535 ports
nmap -p- 10.11.1.22

# Scan for vulnerabilities on specific ports
nmap --script vuln 10.11.1.22 -p 21,80
```
