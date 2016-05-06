# mysql_upgrade

## References
* http://dba.stackexchange.com/questions/97058/mysql-unknown-column-password-last-changed
* http://dev.mysql.com/doc/relnotes/mysql/5.7/en/news-5-7-6.html

##### Run the upgrade 
* *If you upgrade to this release of MySQL from an earlier version, you must run mysql_upgrade (and restart the server) to incorporate the changes to the mysql database.* (http://dev.mysql.com/doc/relnotes/mysql/5.7/en/news-5-7-6.html)
 
```
sudo mysql_upgrade -p
```

