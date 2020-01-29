### DNS Port 53

#### DNS Zone Transfer
```
# Reveal other domains for the domain
dig axfr @ipaddress domainname.com

# After identifying further dns names such as admin.domainname.com add them to your hosts file
nano /etc/hosts
ipaddress   admin.domainname.com other.domainname.com etc.domainname.com
```

#### DNS Discovery
```
host -l <domain.name> <ip address> 
```
