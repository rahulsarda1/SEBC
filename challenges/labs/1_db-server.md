# The command hostname -f and its output
```sh
[root@ip-172-31-84-209 ~]# hostname -f
ip-172-31-84-209.ec2.internal
```
# The command mysql -u <user> -p<password> -e "status;" and its output
```sh
[root@ip-172-31-84-209 ~]# mysql -u root -pbootcamp -e "status;"
--------------
mysql  Ver 15.1 Distrib 5.5.56-MariaDB, for Linux (x86_64) using readline 5.1

Connection id:        11
Current database:
Current user:        root@localhost
SSL:            Not in use
Current pager:        stdout
Using outfile:        ''
Using delimiter:    ;
Server:            MariaDB
Server version:        5.5.56-MariaDB MariaDB Server
Protocol version:    10
Connection:        Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    utf8
Conn.  characterset:    utf8
UNIX socket:        /var/lib/mysql/mysql.sock
Uptime:            13 min 12 sec

Threads: 1  Questions: 51  Slow queries: 0  Opens: 1  Flush tables: 2  Open tables: 27  Queries per second avg: 0.064
--------------
```

# The command mysql -u <user> -p<password> -e "show databases;" and its output
```sh
[root@ip-172-31-84-209 ~]# mysql -u root -pbootcamp -e "show databases;"
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
[root@ip-172-31-84-209 ~]#
```

