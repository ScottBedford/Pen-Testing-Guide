## Privilege Escalation

### If you can modify files as root

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
