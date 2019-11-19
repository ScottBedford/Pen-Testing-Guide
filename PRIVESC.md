### Privilege Escalation

#### If you have found any passwords on the machine, try running as root
```
sudo su
```
#### Check which commands sudo can run
``` 
sudo -l
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
