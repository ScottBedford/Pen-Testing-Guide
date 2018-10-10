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
# Login to mysql
mysql -u root -p

show databases;
use db_name;
show tables;
select * from table_name;
```
