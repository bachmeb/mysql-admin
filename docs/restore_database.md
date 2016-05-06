# restore database

## References
* http://stackoverflow.com/questions/105776/how-do-i-restore-a-mysql-dump-file

### Restore dump file (if the dump file include a CREATE db command at the top)
```
mysql -u <user> -p < db_backup.dump
```

### Alternate method: Restore dump file and specify which database to use
```
mysql -p -u[user] [database] < db_backup.dump
```

### Alternate method: Restore after connecting as root
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
