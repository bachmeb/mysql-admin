# mysqldump

## References
* http://dev.mysql.com/doc/refman/5.7/en/mysqldump.html
* http://stackoverflow.com/questions/105776/how-do-i-restore-a-mysql-dump-file

##### Dump all databases
```
mysqldump -u root -p --all-databases --verbose
```

##### Restore all databases dump file
```
mysql -u <user> -p < db_backup.dump
```

##### Restore all databases dump file
```
mysql> source db_backup.dump;
```
