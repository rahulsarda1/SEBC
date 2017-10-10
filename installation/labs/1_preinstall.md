
ssh -i "ClouderaRahul.pem" ec2-user@ec2-52-55-157-69.compute-1.amazonaws.com
ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-90-86-27.compute-1.amazonaws.com
ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-161-74-89.compute-1.amazonaws.com
ssh -i "ClouderaRahul.pem" ec2-user@ec2-52-23-181-138.compute-1.amazonaws.com
ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-161-96-62.compute-1.amazonaws.com [main]



# Setup sshless access on all machines with public and private key for
ssh-keygen

/home/your-login/.ssh/id_rsa this is private key

copy public key to all machines /home/your-login/.ssh/id_rsa.pub to vi /root/.ssh/authorized_keys

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDIfUZ3xQy3Hq4+pSFDFAcUp5bUpB9yrR/4c1VsDtxoL1dRYRRN+flTXxU2k/k0iE86KQa7LoeGDhqhlthf1LbDT9mTByy50IURvcOZuOdiXvHUwrqJz4VPzlHrVTM79+bb6tupGFmRMYcMlzucZYXoXJSTr3BQ7nZJqedZEaSXe7Ve8BMM7eLpx0P+ew4V5chYWfrvQ2X5N0Ld8smzd3lFSDZBAlMRyd3WEripqXVQ4aQw1C/0BF9fBJ0NBgcLuwvKRGzh8lZ/hpWvF1vYpKc+RQmvkUxo80XcpTFepQF3PeeHLJ/x3iQ9sl/heE1IrxDxAimjGctBV8F4GplgbSTR root@ip-172-31-81-224.ec2.internal

ssh ip-172-31-81-224
ssh ip-172-31-84-109
ssh ip-172-31-95-32
ssh ip-172-31-85-19
ssh ip-172-31-88-78


# 1. On each node as root [swappiness]
sudo root
Put an entry in
vi /etc/sysctl.conf
vm.swappiness = 1


# 2. Currently Mounted File Systems - mount command
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=1826312k,nr_inodes=456578,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=368916k,mode=700,uid=1000,gid=1000)

# 3. Disable transparent hugepage support

Current start of huge pages is disabled.
[root@ip-172-31-81-159 ec2-user]# sysctl vm.nr_hugepages
vm.nr_hugepages = 0

For disabling huge pages we can create services file in systemmd  and then systemctl enable *.service file. Add following command to disable
transparent_hugepage=never
echo never > /sys/kernel/mm/redhat_transparent_hugepage/defrag

# 4. Network interface configuration for one machine
[root@ip-172-31-81-159 ec2-user]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
inet 172.31.81.159  netmask 255.255.240.0  broadcast 172.31.95.255
inet6 fe80::1029:4dff:fea0:4e30  prefixlen 64  scopeid 0x20<link>
ether 12:29:4d:a0:4e:30  txqueuelen 1000  (Ethernet)
RX packets 3546  bytes 311776 (304.4 KiB)
RX errors 0  dropped 0  overruns 0  frame 0
TX packets 2657  bytes 480058 (468.8 KiB)
TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
inet 127.0.0.1  netmask 255.0.0.0
inet6 ::1  prefixlen 128  scopeid 0x10<host>
loop  txqueuelen 0  (Local Loopback)
RX packets 118  bytes 20720 (20.2 KiB)
RX errors 0  dropped 0  overruns 0  frame 0
TX packets 118  bytes 20720 (20.2 KiB)
TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

# Here are some of the prerequisites needed to install Cloudera.. Need Root access or similar account  with all privileges

yum -y install bind*
yum -y install wget
yum -y install nscd
yum -y install ntp

yum -y install perl
yum -y install libaio
yum -y install createrepo
yum -y install yum-utils
yum -y install MySQL-python*
yum -y install python*
yum -y install httpd
yum -y install telnet
yum -y install openssh*
yum -y install rpmdevtools
yum -y install ntp*
yum -y install redhat-lsb*
yum -y install cyrus*
yum -y install mod_ssl*
yum -y install portmap*
yum -y install openssl*
yum -y install mlocate*
yum -y install sshpass*
yum -y remove snappy
yum -y install dos2unix
yum -y install gcc
yum -y install *openldap* migrationtools
yum install -y openldap-clients nss-pam-ldapd
yum install -y sssd*

# 5. Show that forward and reverse host lookups are correctly resolved

For nslookup
yum -y install bind*

## For /etc/hosts, use getent
[root@ip-172-31-81-159 ec2-user]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6

## For DNS, use nslookup
[root@ip-172-31-81-159 ec2-user]# nslookup
> ip-172-31-81-159
Server:        172.31.0.2
Address:    172.31.0.2#53

Non-authoritative answer:
Name:    ip-172-31-81-159.ec2.internal
Address: 172.31.81.159
>

# 6. Show the nscd service is running
yum -y install nscd

service nscd start
```Redirecting to /bin/systemctl start  nscd.service ```

chkconfig nscd on
```Note: Forwarding request to 'systemctl enable nscd.service'.
Created symlink from /etc/systemd/system/multi-user.target.wants/nscd.service to /usr/lib/systemd/system/nscd.service.
Created symlink from /etc/systemd/system/sockets.target.wants/nscd.socket to /usr/lib/systemd/system/nscd.socket.
```


nscd -g
```nscd configuration:

0  server debug level
16s  server runtime
5  current number of threads
32  maximum number of threads
0  number of times clients had to wait
no  paranoia mode enabled
3600  restart internal
5  reload count

....
```

# 7. Show the ntpd service is running

yum -y install ntp

service ntpd start
```Redirecting to /bin/systemctl start  ntpd.service```

chkconfig ntpd on
```Note: Forwarding request to 'systemctl enable ntpd.service'.
Created symlink from /etc/systemd/system/multi-user.target.wants/ntpd.service to /usr/lib/systemd/system/ntpd.service.
```

Synchronize the node.
ntpdate -u <your_ntp_server>

Synchronize the system clock (to prevent synchronization problems).
hwclock --systohc

## If machines are running on same servers
Open the /etc/ntp.conf file and add NTP servers, as in the following example.
server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org

#### [root@ip-172-31-80-185 ~]# sudo ntpq -p
#### remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*jikan.ae7.st    85.29.25.171     2 u    9   64    7   56.474    1.878   0.852
www.heikorichte 192.53.103.108   2 u    5   64    7   96.990   -0.036   1.981
time-b.nist.gov .NIST.           1 u    5   64    7    3.883    0.126   0.873
ip139.ip-5-196- 145.238.203.14   2 u    6   64    7   78.965   -1.564   0.860


# Install MariaDB

# Configure MariaDB with a replica server
## Install MariaDB in both master node and replica node

sudo yum -y install mariadb-server
..
Complete!

sudo service mariadb stop
mkdir mysql_backup
mv /var/lib/mysql/ib_logfile0 ~/mysql_backup/.
mv /var/lib/mysql/ib_logfile1 ~/mysql_backup/.
sudo vi /etc/my.cnf
```
Insert the following into the conf file for the replica. The same can be used for the master, with the only difference in the server_id value, which should be set to 1.

```

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
Enable the mariadb service again
```
sudo systemctl enable mariadb
Created symlink from /etc/systemd/system/multi-user.target.wants/mariadb.service to /usr/lib/systemd/system/mariadb.service.

sudo systemctl list-unit-files | grep mariadb
mariadb.service                             enabled

sudo service mariadb start
Redirecting to /bin/systemctl start  mariadb.service

sudo systemctl status mariadb.service

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

```
Setting up MariaDB
```
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

Setting up MariaDB databases, roles and user grants

```
mysql -u root -p

Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 5.5.56-MariaDB MariaDB Server

Copyright (c) 2000, 2017, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

create database amon DEFAULT CHARACTER SET utf8;
create database rman DEFAULT CHARACTER SET utf8;
create database metastore DEFAULT CHARACTER SET utf8;
create database sentry DEFAULT CHARACTER SET utf8;
create database nav DEFAULT CHARACTER SET utf8;
create database navms DEFAULT CHARACTER SET utf8;
create database hue DEFAULT CHARACTER SET utf8;
create database cmdb DEFAULT CHARACTER SET utf8;

CREATE USER 'mariadbuser'@'ip-172-31-95-76.ec2.internal' identified by 'mariadb';

grant all on cmdb.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on rman.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on metastore.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on sentry.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on nav.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on navms.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on oozie.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';
grant all on hue.* TO 'mariadbuser'@'ip-172-31-95-76.ec2.internal' IDENTIFIED BY 'mariadb';

grant all on cmdb.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on rman.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on metastore.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on sentry.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on nav.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on navms.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on oozie.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';
grant all on hue.* TO 'mariadbuser'@'%' IDENTIFIED BY 'mariadb';

FLUSH PRIVILEGES;
```
Setting up Master

```
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

GRANT REPLICATION SLAVE ON *.* TO 'mariadbuser'@'ip-172-31-94-240.ec2.internal' IDENTIFIED BY 'mariadb';
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
| mysql_binary_log.000004 |     4945 |              |                  |
+-------------------------+----------+--------------+------------------+
1 row in set (0.00 sec)

```

Setting up Replica

```
MariaDB [(none)]> SHOW VARIABLES LIKE 'server_id';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| server_id     | 2     |
+---------------+-------+
1 row in set (0.00 sec)

stop slave;
CHANGE MASTER TO MASTER_HOST='ip-172-31-81-224.ec2.internal' , MASTER_USER='mariadbuser', MASTER_PASSWORD='mariadb', MASTER_LOG_FILE=' mysql_binary_log.000004',MASTER_LOG_POS=4945;
start slave;

MariaDB [(none)]> show slave status;
MariaDB [(none)]> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
Slave_IO_State: Connecting to master
Master_Host: ip-172-31-95-76.ec2.internal
Master_User: mariadbuser
Master_Port: 3306
Connect_Retry: 60
Master_Log_File:  mysql_binary_log.000004
Read_Master_Log_Pos: 423
Relay_Log_File: mariadb-relay-bin.000001
Relay_Log_Pos: 4
Relay_Master_Log_File:  mysql_binary_log.000004
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
Exec_Master_Log_Pos: 423
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

MariaDB [(none)]> \q
Bye
```
```
# Cloudera Manager Prerequisties

ssh ip-172-31-84-109
ssh ip-172-31-95-32
ssh ip-172-31-85-19
ssh ip-172-31-88-78

cd /etc/yum.repos.d/
wget "https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo"

[cloudera-manager]
name = Cloudera Manager, Version 5.9.3
baseurl = https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5.9.3/
gpgkey = https://archive.cloudera.com/redhat/cdh/RPM-GPG-KEY-cloudera
gpgcheck = 1

yum clean all
yum install cloudera-manager-daemons cloudera-manager-server


# Install JDBC Connector

ssh ip-172-31-84-109
ssh ip-172-31-95-32
ssh ip-172-31-85-19
ssh ip-172-31-88-78

wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.44.tar.gz
tar zxvf mysql-connector-java-5.1.44.tar.gz
sudo mkdir -p /usr/share/java/
sudo cp mysql-connector-java-5.1.44/mysql-connector-java-5.1.44-bin.jar /usr/share/java/mysql-connector-java.jar

# Install JDK
wget http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.rpm?AuthParam=1507655469_c90472a279fd9f1ccd0a7a7f5f75e2df
mv jdk-8u144-linux-x64.rpm?AuthParam=1507655469_c90472a279fd9f1ccd0a7a7f5f75e2df jdk-8u144-linux-x64.rpm
yum install jdk-8u144-linux-x64.rpm


# Run Cloudera Manager Database Script

sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql cmdb mariadbuser mariadb -h ip-172-31-81-224.ec2.internal

# Start Cloudera Manager

sudo service cloudera-scm-server start



