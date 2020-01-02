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
