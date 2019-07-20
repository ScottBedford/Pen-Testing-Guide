### SMB
```bash
# Connect to SMB share using smbclient
smbclient //MOUNT/share -I target -N

# Scan smb share using smbmap
smbmap -H xx.xx.xx.xxx
# or
smbmap -H xx.xx.xx.xxx -u anonymous

# Scan smb share using smbclient
smbclient -N -L //xx.xx.xx.xxx

# Mount smb share directly to Linux
mount -t cifs //serverip/sharename /media/windowsshare

```
##
