# mysql service

## References
* http://dev.mysql.com/doc/refman/5.7/en/changing-mysql-user.html

##### Run mysqld as mysql user
```
sudo /sbin/service mysqld start --user=mysql
```

##### Start the Mysql service with the --skip-grant-tables option.
```
sudo /sbin/service mysqld start --skip-grant-tables
```
