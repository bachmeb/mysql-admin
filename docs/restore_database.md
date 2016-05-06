# restore database

## References
* http://stackoverflow.com/questions/105776/how-do-i-restore-a-mysql-dump-file

##### Restore dump file
```
mysql -u <user> -p < db_backup.dump
```

### Alternate method
##### Connect as root
```
mysql -u root -p
```

##### Create the database to be restored and give it a name
```
mysql> create database mydb;
```

##### Use the database
```
mysql> use mydb;
```

##### Use the source command to restore from the dump file
```
mysql> source db_backup.dump;
```
