# CREATE USER

## References
* http://dev.mysql.com/doc/refman/5.7/en/adding-users.html
* http://dba.stackexchange.com/questions/97058/mysql-unknown-column-password-last-changed

##### Connect as root
```
mysql --user=root mysql -p
```

##### 
```
mysql> CREATE USER 'bachmeb'@'localhost' IDENTIFIED BY 'some_pass';
```

##### Exit and run mysql_upgrade, if running CREATE USER returns an error about an unknown column
* [/docs/mysql_upgrade.md](/docs/mysql_upgrade.md)

##### 
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'bachmeb'@'localhost'
    ->     WITH GRANT OPTION;
```

##### 
```
mysql> CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
```

##### 
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%'
    ->     WITH GRANT OPTION;
```

##### 
```
mysql> CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin_pass';
```

##### 
```
mysql> GRANT RELOAD,PROCESS ON *.* TO 'admin'@'localhost';
```

##### 
```
mysql> CREATE USER 'dummy'@'localhost';
```
