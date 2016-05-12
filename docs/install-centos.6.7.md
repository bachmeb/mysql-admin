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

##### Get a link to the IUS repo for mysql57u-server
* https://dl.iuscommunity.org/pub/ius/stable/CentOS/6/x86_64/repoview/mysql57u-server.html

##### Download the IUS repo
```
cd ~
wget https://dl.iuscommunity.org/pub/ius/stable/CentOS/6/x86_64/mysql57u-server-5.7.12-1.ius.centos6.x86_64.rpm
```
```
/*
--2016-05-12 16:11:49--  https://dl.iuscommunity.org/pub/ius/stable/CentOS/6/x86_64/mysql57u-server-5.7.12-1.ius.centos6.x86_64.rpm
Resolving dl.iuscommunity.org... 104.130.201.30, 2001:4801:7827:102:bddb:e4a6:b702:d4ab
Connecting to dl.iuscommunity.org|104.130.201.30|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 21387156 (20M) [application/x-rpm]
Saving to: “mysql57u-server-5.7.12-1.ius.centos6.x86_64.rpm”

100%[=====================================================================================================================>] 21,387,156  4.64M/s   in 4.8s

2016-05-12 16:11:53 (4.29 MB/s) - “mysql57u-server-5.7.12-1.ius.centos6.x86_64.rpm” saved [21387156/21387156]
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
