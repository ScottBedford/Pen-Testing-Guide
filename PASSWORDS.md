### PASSWORD HASHING & CRACKING
#### Identifying hashes
```
# In Kali
hash-identifier
```
#### John the Ripper
```
# Copy /etc/shadow and /etc/passwd into text files and combine them
unshadow passwd.txt shadow.txt > passwords.txt

# Crack with john the ripper
john --wordlist /usr/share/wordlists/sqlmap.txt passwords.txt

# Check if cracked once session finishes
john --show passwords.txt
```
#### Hashcat
```
# Copy just the hashes from /etc/shadow into a file called hashes.txt
hashcat -m 500 -a 3 /usr/share/wordlists/rockyou.txt hashes.txt
```
