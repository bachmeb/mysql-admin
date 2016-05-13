# change password

## References
* http://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html

##### Set root password on localhost
```sql
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('mydb123');
```
