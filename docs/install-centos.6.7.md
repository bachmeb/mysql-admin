# mysql centos 6.7 install

* https://dev.mysql.com/doc/mysql-repo-excerpt/5.6/en/linux-installation-yum-repo.html
* http://superuser.com/questions/603026/mysql-how-to-fix-access-denied-for-user-rootlocalhost
* https://kb.plesk.com/en/128655
* http://serverfault.com/questions/759828/error-while-installing-mysql-on-centos-6-7
* http://stackoverflow.com/questions/1559955/host-xxx-xx-xxx-xxx-is-not-allowed-to-connect-to-this-mysql-server

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
```
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
sudo yum install mysql57u-libs
```
```c
/*
Loaded plugins: fastestmirror, refresh-packagekit
Setting up Install Process
Loading mirror speeds from cached hostfile
 * base: chicago.gaminghost.co
 * epel: mirror.steadfast.net
 * extras: centos.chi.host-engine.com
 * ius: ord.mirror.rackspace.com
 * updates: mirror.steadfast.net
Resolving Dependencies
--> Running transaction check
---> Package mysql57u-libs.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Processing Dependency: mysql57u-common(x86-64) = 5.7.12-1.ius.centos6 for package: mysql57u-libs-5.7.12-1.ius.centos6.x86_64
--> Running transaction check
---> Package mysql57u-common.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Processing Dependency: /etc/my.cnf for package: mysql57u-common-5.7.12-1.ius.centos6.x86_64
--> Running transaction check
---> Package mysql57u-config.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================
 Package                                   Arch                             Version                                        Repository                     Size
===============================================================================================================================================================
Installing:
 mysql57u-libs                             x86_64                           5.7.12-1.ius.centos6                           ius                           902 k
Installing for dependencies:
 mysql57u-common                           x86_64                           5.7.12-1.ius.centos6                           ius                            84 k
 mysql57u-config                           x86_64                           5.7.12-1.ius.centos6                           ius                            56 k

Transaction Summary
===============================================================================================================================================================
Install       3 Package(s)

Total size: 1.0 M
Total download size: 958 k
Installed size: 3.9 M
Is this ok [y/N]: y
Downloading Packages:
(1/2): mysql57u-config-5.7.12-1.ius.centos6.x86_64.rpm                                                                                  |  56 kB     00:00
(2/2): mysql57u-libs-5.7.12-1.ius.centos6.x86_64.rpm                                                                                    | 902 kB     00:00
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                          1.2 MB/s | 958 kB     00:00
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : mysql57u-config-5.7.12-1.ius.centos6.x86_64                                                                                                 1/3
  Installing : mysql57u-common-5.7.12-1.ius.centos6.x86_64                                                                                                 2/3
  Installing : mysql57u-libs-5.7.12-1.ius.centos6.x86_64                                                                                                   3/3
  Verifying  : mysql57u-libs-5.7.12-1.ius.centos6.x86_64                                                                                                   1/3
  Verifying  : mysql57u-config-5.7.12-1.ius.centos6.x86_64                                                                                                 2/3
  Verifying  : mysql57u-common-5.7.12-1.ius.centos6.x86_64                                                                                                 3/3

Installed:
  mysql57u-libs.x86_64 0:5.7.12-1.ius.centos6

Dependency Installed:
  mysql57u-common.x86_64 0:5.7.12-1.ius.centos6                                  mysql57u-config.x86_64 0:5.7.12-1.ius.centos6

Complete!
*/
```

##### Install Mysql Server 5.7
```
sudo yum install mysql57u-server
```
```c
/*
Loaded plugins: fastestmirror, refresh-packagekit
Setting up Install Process
Loading mirror speeds from cached hostfile
 * base: chicago.gaminghost.co
 * epel: mirror.steadfast.net
 * extras: centos.chi.host-engine.com
 * ius: iad.mirror.rackspace.com
 * updates: mirror.steadfast.net
Resolving Dependencies
--> Running transaction check
---> Package mysql57u-server.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Processing Dependency: mysql57u-errmsg(x86-64) = 5.7.12-1.ius.centos6 for package: mysql57u-server-5.7.12-1.ius.centos6.x86_64
--> Processing Dependency: mysql-compat-client(x86-64) for package: mysql57u-server-5.7.12-1.ius.centos6.x86_64
--> Processing Dependency: mysql(x86-64) for package: mysql57u-server-5.7.12-1.ius.centos6.x86_64
--> Processing Dependency: liblz4.so.1()(64bit) for package: mysql57u-server-5.7.12-1.ius.centos6.x86_64
--> Processing Dependency: libevent-1.4.so.2()(64bit) for package: mysql57u-server-5.7.12-1.ius.centos6.x86_64
--> Running transaction check
---> Package libevent.x86_64 0:1.4.13-4.el6 will be installed
---> Package lz4.x86_64 0:r131-1.el6 will be installed
---> Package mysql57u.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Processing Dependency: mysqlclient16 for package: mysql57u-5.7.12-1.ius.centos6.x86_64
---> Package mysql57u-errmsg.x86_64 0:5.7.12-1.ius.centos6 will be installed
--> Running transaction check
---> Package mysqlclient16.x86_64 0:5.1.61-4.ius.centos6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================
 Package                                  Arch                            Version                                          Repository                     Size
===============================================================================================================================================================
Installing:
 mysql57u-server                          x86_64                          5.7.12-1.ius.centos6                             ius                            20 M
Installing for dependencies:
 libevent                                 x86_64                          1.4.13-4.el6                                     base                           66 k
 lz4                                      x86_64                          r131-1.el6                                       epel                           63 k
 mysql57u                                 x86_64                          5.7.12-1.ius.centos6                             ius                           9.6 M
 mysql57u-errmsg                          x86_64                          5.7.12-1.ius.centos6                             ius                           322 k
 mysqlclient16                            x86_64                          5.1.61-4.ius.centos6                             ius                           1.4 M

Transaction Summary
===============================================================================================================================================================
Install       6 Package(s)

Total size: 32 M
Total download size: 21 M
Installed size: 140 M
Is this ok [y/N]: y

Downloading Packages:
(1/3): libevent-1.4.13-4.el6.x86_64.rpm                                                                                                 |  66 kB     00:00
(2/3): mysql57u-errmsg-5.7.12-1.ius.centos6.x86_64.rpm                                                                                  | 322 kB     00:00
(3/3): mysql57u-server-5.7.12-1.ius.centos6.x86_64.rpm                                                                                  |  20 MB     00:16
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                          1.2 MB/s |  21 MB     00:17
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : lz4-r131-1.el6.x86_64                                                                                                                       1/6
  Installing : libevent-1.4.13-4.el6.x86_64                                                                                                                2/6
  Installing : mysqlclient16-5.1.61-4.ius.centos6.x86_64                                                                                                   3/6
  Installing : mysql57u-5.7.12-1.ius.centos6.x86_64                                                                                                        4/6
  Installing : mysql57u-errmsg-5.7.12-1.ius.centos6.x86_64                                                                                                 5/6
  Installing : mysql57u-server-5.7.12-1.ius.centos6.x86_64                                                                                                 6/6
  Verifying  : mysql57u-errmsg-5.7.12-1.ius.centos6.x86_64                                                                                                 1/6
  Verifying  : mysqlclient16-5.1.61-4.ius.centos6.x86_64                                                                                                   2/6
  Verifying  : libevent-1.4.13-4.el6.x86_64                                                                                                                3/6
  Verifying  : mysql57u-5.7.12-1.ius.centos6.x86_64                                                                                                        4/6
  Verifying  : mysql57u-server-5.7.12-1.ius.centos6.x86_64                                                                                                 5/6
  Verifying  : lz4-r131-1.el6.x86_64                                                                                                                       6/6

Installed:
  mysql57u-server.x86_64 0:5.7.12-1.ius.centos6

Dependency Installed:
  libevent.x86_64 0:1.4.13-4.el6               lz4.x86_64 0:r131-1.el6  mysql57u.x86_64 0:5.7.12-1.ius.centos6  mysql57u-errmsg.x86_64 0:5.7.12-1.ius.centos6
  mysqlclient16.x86_64 0:5.1.61-4.ius.centos6

Complete!
*/
```

##### List all of the installed mysql packages
```
sudo yum list installed | grep mysql
```

##### Check the status of the mysqld service
```
sudo /sbin/service mysqld status
```
```c
/*
mysqld is stopped
*/
```

##### Start the Mysql service with the --skip-grant-tables option.
```
sudo /sbin/service mysqld start --skip-grant-tables
```
```c
/*
Initializing MySQL database
Starting mysqld:                                           [  OK  ]
*/
```

##### Connect as root
```
mysql -u root mysql
```

##### UPDATE the Password
```
mysql> UPDATE user SET Password=PASSWORD('my_password') where USER='root';
```

##### If UPDATE Password fails, try UPDATE authentication_string
```
mysql> UPDATE user SET authentication_string=password('my_password') where user='root';
```

##### Flush privileges
```
mysql> FLUSH PRIVILEGES;
```

##### Exit
```
mysql> exit
```

##### Restart the instance/daemon without the --skip-grant-tables option.
```
sudo /sbin/service mysqld restart
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

##### Create a user who can connect to the mysql server from a remote host
```
mysql> CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%'
    -> WITH GRANT OPTION;
```
