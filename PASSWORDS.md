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
john --wordlist=/usr/share/wordlists/rockyou.txt --rules passwords.txt 

# Check if cracked once session finishes
john --show passwords.txt
```
#### John alternate method
```
# Save your password in a file called temp
john temp --wordlist=/usr/share/wordlists/rockyou.txt --fork=4
```
#### John with RAR/ZIP
```
# Get password hash for zip file
zip2john filename.zip > hash.txt 
john --format=zip hash.txt 

# Get password hash for rar file
rar2john filename.rar > hash.txt
john --format=rar hash.txt
```

#### John direct cracking
```
john /etc/shadow
```

#### Hashcat
```
# Copy just the hashes from /etc/shadow into a file called hashes.txt
hashcat -m 500 -a 3 /usr/share/wordlists/rockyou.txt hashes.txt
```

#### Windows SAM
```
# Use samdump2 from Windows/System32/config
samdump2 SYSTEM SAM

# Send the second part of the hash to hashkiller.co.uk
Username:1000:aad3b435b51404eeaad3b435b51404ee:<this>26112010952d963c8dc4217daec986d9</this>:::
```


