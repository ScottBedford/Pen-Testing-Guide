## SQL Penetration Testing Techniques

### Locate the localhost file making connection to the SQL
```
# Grep for localhost
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
