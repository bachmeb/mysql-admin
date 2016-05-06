# CREATE USER

## References
* http://dev.mysql.com/doc/refman/5.7/en/adding-users.html
* http://dba.stackexchange.com/questions/97058/mysql-unknown-column-password-last-changed

##### Connect as root
```
mysql --user=root mysql -p
```

##### Create a user that can connect only from localhost
```
mysql> CREATE USER 'bachmeb'@'localhost' IDENTIFIED BY 'some_pass';
```

##### Exit and run mysql_upgrade, if running CREATE USER returns an error about an unknown column
* [/docs/mysql_upgrade.md](/docs/mysql_upgrade.md)

##### Grant all privileges to the user that can connect only from localhost
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'bachmeb'@'localhost'
    ->     WITH GRANT OPTION;
```

##### Create a user that can connect from any host
```
mysql> CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
```

##### Grant all privileges to the user that can connect from any host
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%'
    ->     WITH GRANT OPTION;
```

##### Craete and account that can only be used by admin to connect from the local host
```
mysql> CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin_pass';
```

##### Granted admin the RELOAD and PROCESS administrative privileges
```
mysql> GRANT RELOAD,PROCESS ON *.* TO 'admin'@'localhost';
```

##### Craete an account that has no password (which is insecure and not recommended)
```
mysql> CREATE USER 'dummy'@'localhost';
```
