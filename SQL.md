## SQL Penetration Testing Techniques

### SQLMAP
```
sqlmap -u "http://domain.com"
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
