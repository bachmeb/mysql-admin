# CREATE USER

## References
* http://dev.mysql.com/doc/refman/5.7/en/adding-users.html
* http://dba.stackexchange.com/questions/97058/mysql-unknown-column-password-last-changed
* http://stackoverflow.com/questions/1135245/how-to-get-a-list-of-mysql-user-accounts

##### Connect as root
```
mysql -u root mysql -p
```

##### List all users
```sql
mysql> SELECT User FROM mysql.user;
```

##### Describe the mysql.user table
```sql
mysql> desc mysql.user;
```
```
+------------------------+-----------------------------------+------+-----+-----------------------+-------+
| Field                  | Type                              | Null | Key | Default               | Extra |
+------------------------+-----------------------------------+------+-----+-----------------------+-------+
| Host                   | char(60)                          | NO   | PRI |                       |       |
| User                   | char(32)                          | NO   | PRI |                       |       |
| Select_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Insert_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Update_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Delete_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Create_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Drop_priv              | enum('N','Y')                     | NO   |     | N                     |       |
| Reload_priv            | enum('N','Y')                     | NO   |     | N                     |       |
| Shutdown_priv          | enum('N','Y')                     | NO   |     | N                     |       |
| Process_priv           | enum('N','Y')                     | NO   |     | N                     |       |
| File_priv              | enum('N','Y')                     | NO   |     | N                     |       |
| Grant_priv             | enum('N','Y')                     | NO   |     | N                     |       |
| References_priv        | enum('N','Y')                     | NO   |     | N                     |       |
| Index_priv             | enum('N','Y')                     | NO   |     | N                     |       |
| Alter_priv             | enum('N','Y')                     | NO   |     | N                     |       |
| Show_db_priv           | enum('N','Y')                     | NO   |     | N                     |       |
| Super_priv             | enum('N','Y')                     | NO   |     | N                     |       |
| Create_tmp_table_priv  | enum('N','Y')                     | NO   |     | N                     |       |
| Lock_tables_priv       | enum('N','Y')                     | NO   |     | N                     |       |
| Execute_priv           | enum('N','Y')                     | NO   |     | N                     |       |
| Repl_slave_priv        | enum('N','Y')                     | NO   |     | N                     |       |
| Repl_client_priv       | enum('N','Y')                     | NO   |     | N                     |       |
| Create_view_priv       | enum('N','Y')                     | NO   |     | N                     |       |
| Show_view_priv         | enum('N','Y')                     | NO   |     | N                     |       |
| Create_routine_priv    | enum('N','Y')                     | NO   |     | N                     |       |
| Alter_routine_priv     | enum('N','Y')                     | NO   |     | N                     |       |
| Create_user_priv       | enum('N','Y')                     | NO   |     | N                     |       |
| Event_priv             | enum('N','Y')                     | NO   |     | N                     |       |
| Trigger_priv           | enum('N','Y')                     | NO   |     | N                     |       |
| Create_tablespace_priv | enum('N','Y')                     | NO   |     | N                     |       |
| ssl_type               | enum('','ANY','X509','SPECIFIED') | NO   |     |                       |       |
| ssl_cipher             | blob                              | YES  |     | NULL                  |       |
| x509_issuer            | blob                              | YES  |     | NULL                  |       |
| x509_subject           | blob                              | YES  |     | NULL                  |       |
| max_questions          | int(11) unsigned                  | NO   |     | 0                     |       |
| max_updates            | int(11) unsigned                  | NO   |     | 0                     |       |
| max_connections        | int(11) unsigned                  | NO   |     | 0                     |       |
| max_user_connections   | int(11) unsigned                  | NO   |     | 0                     |       |
| plugin                 | char(64)                          | NO   |     | mysql_native_password |       |
| authentication_string  | text                              | YES  |     | NULL                  |       |
| password_expired       | enum('N','Y')                     | NO   |     | N                     |       |
| password_last_changed  | timestamp                         | YES  |     | NULL                  |       |
| password_lifetime      | smallint(5) unsigned              | YES  |     | NULL                  |       |
| account_locked         | enum('N','Y')                     | NO   |     | N                     |       |
+------------------------+-----------------------------------+------+-----+-----------------------+-------+
```

##### Create a user that can connect only from localhost
```sql
mysql> CREATE USER 'bachmeb'@'localhost' IDENTIFIED BY 'some_pass';
```

##### Exit and run mysql_upgrade, if running CREATE USER returns an error about an unknown column
* [/docs/mysql_upgrade.md](/docs/mysql_upgrade.md)

##### Grant all privileges to the user that can connect only from localhost
```sql
mysql> GRANT ALL PRIVILEGES ON *.* TO 'bachmeb'@'localhost' WITH GRANT OPTION;
```

##### Craete an account that can connect only from localhost and has no password (which is insecure and not recommended)
```sql
mysql> CREATE USER 'dummy'@'localhost';
```

##### Create a user that can connect from any host
```sql
mysql> CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
```
##### See the user
```
select * from user where User='monty';
```
##### Grant all privileges to the user that can connect from any host
```sql
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%' WITH GRANT OPTION;
```
##### See the user
```
select * from user where User='monty';
```
##### Granted admin the RELOAD and PROCESS administrative privileges
* *These privileges enable the admin user to execute the mysqladmin reload, mysqladmin refresh, and mysqladmin flush-xxx commands, as well as mysqladmin processlist.* (http://dev.mysql.com/doc/refman/5.7/en/adding-users.html)
```
mysql> GRANT RELOAD,PROCESS ON *.* TO 'admin'@'localhost';
```

