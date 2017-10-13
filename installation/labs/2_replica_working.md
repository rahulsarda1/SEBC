# Install MariaDB on following nodes
```sh
ssh ip-172-31-90-35
ssh ip-172-31-95-78
```
# Configure MariaDB with a replica server

## Install MariaDB in both master node and replica node

```sh
sudo yum -y install mariadb-server
sudo service mariadb stop
mkdir mysql_backup
mv /var/lib/mysql/ib_logfile0 ~/mysql_backup/.
mv /var/lib/mysql/ib_logfile1 ~/mysql_backup/.
sudo vi /etc/my.cnf
```
## Insert the following into the conf file for the replica. The same can be used for the master, with the only difference in the server_id value, which should be set to 1.

```sh
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0
server_id=1
key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log

binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mariadb/mariadb.log
pid-file=/var/run/mariadb/mariadb.pid
```
## Enable the mariadb service again
```sh
sudo systemctl enable mariadb
Created symlink from /etc/systemd/system/multi-user.target.wants/mariadb.service to /usr/lib/systemd/system/mariadb.service.

sudo systemctl list-unit-files | grep mariadb
mariadb.service                             enabled

sudo service mariadb start
Redirecting to /bin/systemctl start  mariadb.service

sudo systemctl status mariadb.service
```
● mariadb.service - MariaDB database server
Loaded: loaded (/usr/lib/systemd/system/mariadb.service; enabled; vendor preset: disabled)
Active: active (running) since Mon 2017-10-09 22:43:08 EDT; 9s ago
Process: 9952 ExecStartPost=/usr/libexec/mariadb-wait-ready $MAINPID (code=exited, status=0/SUCCESS)
Process: 9874 ExecStartPre=/usr/libexec/mariadb-prepare-db-dir %n (code=exited, status=0/SUCCESS)
Main PID: 9951 (mysqld_safe)
CGroup: /system.slice/mariadb.service
├─ 9951 /bin/sh /usr/bin/mysqld_safe --basedir=/usr
└─10362 /usr/libexec/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --log-error=/var/log/mariadb/mariadb.log --pid-file=/var/run/mariadb/mariadb.pid

Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: MySQL manual for more instructions.
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: Please report any problems at http://mariadb.org/jira
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: The latest information about MariaDB is available at http://mariadb.org/.
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: You can find additional information about the MySQL part at:
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: http://dev.mysql.com
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: Consider joining MariaDB's strong and vibrant community:
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mariadb-prepare-db-dir[9874]: https://mariadb.org/get-involved/
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mysqld_safe[9951]: 171009 22:42:49 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
Oct 09 22:42:49 ip-172-31-95-76.ec2.internal mysqld_safe[9951]: 171009 22:42:49 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
Oct 09 22:43:08 ip-172-31-95-76.ec2.internal systemd[1]: Started MariaDB database server.


## Setting up Secure installation

```sh
sudo /usr/bin/mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] Y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
... skipping.

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
- Dropping test database...
... Success!
- Removing privileges on test database...
... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```

## Setting up MariaDB databases, roles and user grants ( Issue - each user should be different for different database )

```sh
mysql -u root -p

Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 5.5.56-MariaDB MariaDB Server

Copyright (c) 2000, 2017, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

create database amon DEFAULT CHARACTER SET utf8;
create database rman DEFAULT CHARACTER SET utf8;
create database hive DEFAULT CHARACTER SET utf8;
create database sentry DEFAULT CHARACTER SET utf8;
create database nav DEFAULT CHARACTER SET utf8;
create database navms DEFAULT CHARACTER SET utf8;
create database hue DEFAULT CHARACTER SET utf8;
create database cmdb DEFAULT CHARACTER SET utf8;
create database oozie DEFAULT CHARACTER SET utf8;

https://www.cloudera.com/documentation/enterprise/5-5-x/topics/install_cm_mariadb.html

CREATE USER 'amon'@'%' identified by 'mariadb';
CREATE USER 'rman'@'%' identified by 'mariadb';
CREATE USER 'hive'@'%' identified by 'mariadb';
CREATE USER 'sentry'@'%' identified by 'mariadb';
CREATE USER 'nav'@'%' identified by 'mariadb';
CREATE USER 'navms'@'%' identified by 'mariadb';
CREATE USER 'hue'@'%' identified by 'mariadb';
CREATE USER 'cmdb'@'%' identified by 'mariadb';;
CREATE USER 'oozie'@'%' identified by 'mariadb'

grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'mariadb';
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'mariadb';
grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'mariadb';
grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'mariadb';
grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'mariadb';
grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'mariadb';
grant all on hue.* TO 'hue'@'%' IDENTIFIED BY 'mariadb';
grant all on cmdb.* TO 'cmdb'@'%' IDENTIFIED BY 'mariadb';
grant all on oozie.* TO 'oozie'@'%' IDENTIFIED BY 'mariadb';


FLUSH PRIVILEGES;
```
## Setting up Master details

```sh
MariaDB [(none)]> SHOW GRANTS FOR mariadbuser
+------------------------------------------------------------------------------------------------------------+
| Grants for mariadbuser@%                                                                                   |
+------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mariadbuser'@'%' IDENTIFIED BY PASSWORD '*54958E764CE10E50764C2EECBB71D01F08549980' |
| GRANT ALL PRIVILEGES ON `oozie`.* TO 'mariadbuser'@'%'                                                     |
| GRANT ALL PRIVILEGES ON `navms`.* TO 'mariadbuser'@'%'                                                     |
| GRANT ALL PRIVILEGES ON `nav`.* TO 'mariadbuser'@'%'                                                       |
| GRANT ALL PRIVILEGES ON `sentry`.* TO 'mariadbuser'@'%'                                                    |
| GRANT ALL PRIVILEGES ON `metastore`.* TO 'mariadbuser'@'%'                                                 |
| GRANT ALL PRIVILEGES ON `rman`.* TO 'mariadbuser'@'%'                                                      |
| GRANT ALL PRIVILEGES ON `cmdb`.* TO 'mariadbuser'@'%'                                                      |
| GRANT ALL PRIVILEGES ON `hue`.* TO 'mariadbuser'@'%'                                                       |
+------------------------------------------------------------------------------------------------------------+

2 rows in set (0.00 sec)

GRANT REPLICATION SLAVE ON *.* TO 'mariadbuser'@'ip-172-31-95-78.ec2.internal' IDENTIFIED BY 'mariadb';
SET GLOBAL binlog_format = 'ROW';
FLUSH TABLES WITH READ LOCK;

SHOW GLOBAL VARIABLES like 'server\_id';

+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| server_id     | 1     |
+---------------+-------+
1 row in set (0.00 sec)

MariaDB [(none)]> SHOW MASTER STATUS;
+-------------------------+----------+--------------+------------------+
| File                    | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+-------------------------+----------+--------------+------------------+
| mysql_binary_log.000003 |     5085 |              |                  |
+-------------------------+----------+--------------+------------------+
1 row in set (0.00 sec)

# Master script post setting up replica
UNLOCK TABLES;
```

# Setting up Replica (issue yet to setup the replica correctly)

```sh
MariaDB [(none)]> SHOW VARIABLES LIKE 'server_id';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| server_id     | 2     |
+---------------+-------+
1 row in set (0.00 sec)

stop slave;
CHANGE MASTER TO MASTER_HOST='ip-172-31-95-78.ec2.internal' , MASTER_USER='mariadbuser', MASTER_PASSWORD='mariadb', MASTER_LOG_FILE='mysql_binary_log.000003',MASTER_LOG_POS=5262;
start slave;

show slave status;
MariaDB [(none)]> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
Slave_IO_State: Connecting to master
Master_Host: ip-172-31-91-58.ec2.internal
Master_User: mariadbuser
Master_Port: 3306
Connect_Retry: 60
Master_Log_File:  mysql_binary_log.000003
Read_Master_Log_Pos: 4049
Relay_Log_File: mariadb-relay-bin.000001
Relay_Log_Pos: 4
Relay_Master_Log_File:  mysql_binary_log.000003
Slave_IO_Running: Connecting
Slave_SQL_Running: Yes
Replicate_Do_DB:
Replicate_Ignore_DB:
Replicate_Do_Table:
Replicate_Ignore_Table:
Replicate_Wild_Do_Table:
Replicate_Wild_Ignore_Table:
Last_Errno: 0
Last_Error:
Skip_Counter: 0
Exec_Master_Log_Pos: 4049
Relay_Log_Space: 245
Until_Condition: None
Until_Log_File:
Until_Log_Pos: 0
Master_SSL_Allowed: No
Master_SSL_CA_File:
Master_SSL_CA_Path:
Master_SSL_Cert:
Master_SSL_Cipher:
Master_SSL_Key:
Seconds_Behind_Master: NULL
Master_SSL_Verify_Server_Cert: No
Last_IO_Errno: 0
Last_IO_Error:
Last_SQL_Errno: 0
Last_SQL_Error:
Replicate_Ignore_Server_Ids:
Master_Server_Id: 0
1 row in set (0.00 sec)

MariaDB [(none)]> exit
Bye
```

