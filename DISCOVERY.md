### Discovery
#### Network
```
netdiscover -r xx.xx.xx.0/24

arp-scan -l
```
#### Nmap
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

# Scan UDP
nmap <ip> -sU
```
#### Masscan
```
masscan -p1-65535 --rate 1000 <ip> 
```
#### Hostname
```
nmblookup -A 10.11.1.115
```
#### Netcat
```
# Scan port 25 and check if open
nc -nv 10.11.1.120 25	
HELP

# Scan 110 for POP3 credentials and if open
nc -nv 10.11.1.120 110
USER bob
PASS bob
QUIT

# Scan IMAP port
nc -nv 10.11.1.120 143
```
