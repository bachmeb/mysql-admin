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

##### Search for mysql libs
```
sudo yum search mysql | grep libs
```
```c
/*
mysql-libs.i686 : The shared libraries required for MySQL clients
mysql-libs.x86_64 : The shared libraries required for MySQL clients
mysql55-libs.x86_64 : The shared libraries required for MySQL clients
mysql56u-libs.x86_64 : The shared libraries required for MySQL clients
mysql57u-libs.x86_64 : The shared libraries required for MySQL clients
*/
```

##### Erase 
```
sudo yum erase mysql-libs
```c
/*
Loaded plugins: fastestmirror, refresh-packagekit
Setting up Remove Process
Resolving Dependencies
--> Running transaction check
---> Package mysql-libs.x86_64 0:5.1.73-5.el6_7.1 will be erased
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Processing Dependency: mysql-libs for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Running transaction check
---> Package postfix.x86_64 2:2.6.6-6.el6_7.1 will be erased
--> Processing Dependency: /usr/sbin/sendmail for package: redhat-lsb-core-4.0-7.el6.centos.x86_64
--> Processing Dependency: /usr/sbin/sendmail for package: cronie-1.4.4-15.el6_7.1.x86_64
--> Running transaction check
---> Package cronie.x86_64 0:1.4.4-15.el6_7.1 will be erased
--> Processing Dependency: cronie = 1.4.4-15.el6_7.1 for package: cronie-anacron-1.4.4-15.el6_7.1.x86_64
---> Package redhat-lsb-core.x86_64 0:4.0-7.el6.centos will be erased
--> Processing Dependency: redhat-lsb-core(x86-64) = 4.0 for package: redhat-lsb-printing-4.0-7.el6.centos.x86_64
--> Processing Dependency: redhat-lsb-core(x86-64) = 4.0 for package: redhat-lsb-graphics-4.0-7.el6.centos.x86_64
--> Running transaction check
---> Package cronie-anacron.x86_64 0:1.4.4-15.el6_7.1 will be erased
---> Package redhat-lsb-graphics.x86_64 0:4.0-7.el6.centos will be erased
---> Package redhat-lsb-printing.x86_64 0:4.0-7.el6.centos will be erased
--> Processing Dependency: /etc/cron.d for package: crontabs-1.10-33.el6.noarch
--> Processing Dependency: /etc/cron.d for package: sysstat-9.0.4-27.el6.x86_64
--> Restarting Dependency Resolution with new changes.
--> Running transaction check
---> Package crontabs.noarch 0:1.10-33.el6 will be erased
---> Package sysstat.x86_64 0:9.0.4-27.el6 will be erased
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================
 Package                             Arch                   Version                             Repository                                                Size
===============================================================================================================================================================
Removing:
 mysql-libs                          x86_64                 5.1.73-5.el6_7.1                    @updates                                                 4.0 M
Removing for dependencies:
 cronie                              x86_64                 1.4.4-15.el6_7.1                    @updates                                                 174 k
 cronie-anacron                      x86_64                 1.4.4-15.el6_7.1                    @updates                                                  43 k
 crontabs                            noarch                 1.10-33.el6                         @anaconda-CentOS-201508042137.x86_64/6.7                 2.4 k
 postfix                             x86_64                 2:2.6.6-6.el6_7.1                   @updates                                                 9.7 M
 redhat-lsb-core                     x86_64                 4.0-7.el6.centos                    @base                                                     22 k
 redhat-lsb-graphics                 x86_64                 4.0-7.el6.centos                    @base                                                    0.0
 redhat-lsb-printing                 x86_64                 4.0-7.el6.centos                    @base                                                    0.0
 sysstat                             x86_64                 9.0.4-27.el6                        @base                                                    825 k

Transaction Summary
===============================================================================================================================================================
Remove        9 Package(s)

Installed size: 15 M
Is this ok [y/N]: y
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
Warning: RPMDB altered outside of yum.
  Erasing    : redhat-lsb-graphics-4.0-7.el6.centos.x86_64                                                                                                 1/9
  Erasing    : redhat-lsb-printing-4.0-7.el6.centos.x86_64                                                                                                 2/9
  Erasing    : redhat-lsb-core-4.0-7.el6.centos.x86_64                                                                                                     3/9
/var/tmp/rpm-tmp.FT50wp: line 1: lsb_release: command not found
  Erasing    : sysstat-9.0.4-27.el6.x86_64                                                                                                                 4/9
  Erasing    : crontabs-1.10-33.el6.noarch                                                                                                                 5/9
  Erasing    : cronie-anacron-1.4.4-15.el6_7.1.x86_64                                                                                                      6/9
  Erasing    : cronie-1.4.4-15.el6_7.1.x86_64                                                                                                              7/9
  Erasing    : 2:postfix-2.6.6-6.el6_7.1.x86_64                                                                                                            8/9
  Erasing    : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                          9/9
  Verifying  : cronie-1.4.4-15.el6_7.1.x86_64                                                                                                              1/9
  Verifying  : cronie-anacron-1.4.4-15.el6_7.1.x86_64                                                                                                      2/9
  Verifying  : redhat-lsb-printing-4.0-7.el6.centos.x86_64                                                                                                 3/9
  Verifying  : redhat-lsb-core-4.0-7.el6.centos.x86_64                                                                                                     4/9
  Verifying  : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                          5/9
  Verifying  : sysstat-9.0.4-27.el6.x86_64                                                                                                                 6/9
  Verifying  : crontabs-1.10-33.el6.noarch                                                                                                                 7/9
  Verifying  : redhat-lsb-graphics-4.0-7.el6.centos.x86_64                                                                                                 8/9
  Verifying  : 2:postfix-2.6.6-6.el6_7.1.x86_64                                                                                                            9/9

Removed:
  mysql-libs.x86_64 0:5.1.73-5.el6_7.1

Dependency Removed:
  cronie.x86_64 0:1.4.4-15.el6_7.1                      cronie-anacron.x86_64 0:1.4.4-15.el6_7.1          crontabs.noarch 0:1.10-33.el6
  postfix.x86_64 2:2.6.6-6.el6_7.1                      redhat-lsb-core.x86_64 0:4.0-7.el6.centos         redhat-lsb-graphics.x86_64 0:4.0-7.el6.centos
  redhat-lsb-printing.x86_64 0:4.0-7.el6.centos         sysstat.x86_64 0:9.0.4-27.el6

Complete!
*/
```

##### Install the 5.7 version of mysql-libs
```

```

##### Install Mysql Community Server
```
sudo yum install mysqlasdfasdfasdfasdf
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
