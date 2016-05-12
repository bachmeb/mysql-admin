# mysql rhel 5.11

## References
* https://dev.mysql.com/doc/mysql-repo-excerpt/5.6/en/linux-installation-yum-repo.html
* http://superuser.com/questions/603026/mysql-how-to-fix-access-denied-for-user-rootlocalhost

##### See if a MySQL Yum repository has already been added
```
yum repolist enabled | grep "mysql.*-community.*"
```
```
ls -l /etc/yum.repos.d/
```
##### Download MySQL Yum Repository
* http://dev.mysql.com/downloads/repo/yum/
  * Red Hat Enterprise Linux 5 / Oracle Linux 5 (Architecture Independent), RPM Package
    * mysql57-community-release-el5-7.noarch.rpm

##### Install the downloaded release package
```
sudo rpm -Uvh mysql57-community-release-{ MAKE SURE YOU ARE USING THE CORRECT VERSION FOR YOUR OS }.noarch.rpm
```

##### Check that the MySQL Yum repository has been successfully added
```
yum repolist enabled | grep "mysql.*-community.*"
```

##### Install Mysql Community Server
```
sudo yum install mysql-community-server
```

##### Start the Mysql service with the --skip-grant-tables option.
```
sudo /sbin/service mysqld start --skip-grant-tables
```

##### Connect as root
```
mysql -u root mysql
```

##### UPDATE the Password
```
UPDATE user SET Password=PASSWORD('my_password') where USER='root';
```

##### If UPDATE Password fails, try UPDATE authentication_string
```
UPDATE user SET authentication_string=password('my_password') where user='root';
```

##### Flush privileges
```
FLUSH PRIVILEGES;
```

##### Restart the instance/daemon without the --skip-grant-tables option.
```
sudo /sbin/service mysql restart
```

##### Secure the Mysql installation
```
mysql_secure_installation
```
```c
/*
Securing the MySQL server deployment.

Enter password for user root:

The existing password for the user account root has expired. Please set a new password.

New password:

Re-enter new password:
The 'validate_password' plugin is installed on the server.
The subsequent steps will run with the existing configuration
of the plugin.
Using existing password for root.

Estimated strength of the password: 25
Change the password for root ? ((Press y|Y for Yes, any other key for No) : y

New password:

Re-enter new password:

Estimated strength of the password: 100
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : y
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
Success.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : y
Success.

By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
Success.

All done!
*/
```

##### Connect to mysql as root with the new password
```
mysql -u root -p
```
