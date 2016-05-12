# mysql centos 6.7 install

* https://dev.mysql.com/doc/mysql-repo-excerpt/5.6/en/linux-installation-yum-repo.html
* http://superuser.com/questions/603026/mysql-how-to-fix-access-denied-for-user-rootlocalhost
* https://kb.plesk.com/en/128655
* http://serverfault.com/questions/759828/error-while-installing-mysql-on-centos-6-7

##### See if a MySQL Yum repository has already been added
```
yum repolist enabled | grep "mysql.*-community.*"
```
```
ls -l /etc/yum.repos.d/
```

##### Add the IUS repo
* https://github.com/bachmeb/linux-admin/blob/master/docs/ius/centos.6.7.md

##### Search for mysql server
```
sudo yum search mysql | grep server
```
```c
/*
dpm-copy-server-mysql.x86_64 : DPM copy server with MySQL database back-end
dpm-name-server-mysql.x86_64 : DPM name server with MySQL database back-end
dpm-server-mysql.x86_64 : Disk Pool Manager (DPM) server with MySQL database
dpm-srm-server-mysql.x86_64 : DPM SRM server with MySQL database back-end
lfc-server-mysql.x86_64 : LCG File Catalog (LFC) server with MySQL database
mod_auth_mysql.x86_64 : Basic authentication for the Apache web server using a
mysql-server.x86_64 : The MySQL server and related files
mysql55-server.x86_64 : The MySQL server and related files
mysql56u-common.x86_64 : The shared files required for MySQL server and client
mysql56u-server.x86_64 : The MySQL server and related files
mysql57u-common.x86_64 : The shared files required for MySQL server and client
mysql57u-server.x86_64 : The MySQL server and related files
proftpd-mysql.x86_64 : Module to add MySQL support to the ProFTPD FTP server
voms-mysql-plugin.x86_64 : VOMS server plugin for MySQL
zabbix-server-mysql.x86_64 : Zabbix server compiled to use MySQL
zabbix20-server-mysql.x86_64 : Zabbix server compiled to use MySQL
zabbix22-server-mysql.x86_64 : Zabbix server compiled to use MySQL
mysql57u-config.x86_64 : The config files required by server and client
mysql57u-errmsg.x86_64 : The error messages files required by server and
*/
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
