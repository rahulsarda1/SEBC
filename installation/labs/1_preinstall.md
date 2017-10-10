
ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-158-233-109.compute-1.amazonaws.com [Main]

ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-210-247-0.compute-1.amazonaws.com

ssh -i "ClouderaRahul.pem" ec2-user@ec2-54-90-76-165.compute-1.amazonaws.com

ssh -i "ClouderaRahul.pem" ec2-user@ec2-52-91-87-42.compute-1.amazonaws.com

ssh -i "ClouderaRahul.pem" ec2-user@ec2-34-227-163-74.compute-1.amazonaws.com



# Setup sshless access on all machines with public and private key for
ssh-keygen

/home/your-login/.ssh/id_rsa this is private key

copy public key to all machines /root/.ssh/id_rsa.pub
to
vi /root/.ssh/authorized_keys

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDiEtf/5fUtRZ+CbtfTLbbgSPRhsWQiV3oL+3TQbyktFTJpwQNtCt1Z3rr0V7hk/2mOINDCqrUMfmagbcr8slFe5fp49AC30IhNrYB5ownfwrkaaujhR/Mw5SQv4eS0fbTCjOk8sIGsSsaws2fKNRtkmXTX3W3VMEqUZrmEgrho7KrP1131tLGvBcynpDAwMKspdDawyluhsU3tLdERGuHzoBTgLI5fP2xFHCG5h8qaBHtwKfu21dw9sTwflTs7b7n21OuEtRkMLyk6ZpeqKsexceOvGLAxWskkNxTgm568fwmJT9Mz58lCSGVt3QVbkRyKghkvulWKHKPzr9gtxuP root@ip-172-31-91-58.ec2.internal

[main]
ssh ip-172-31-91-58
ssh ip-172-31-89-46
ssh ip-172-31-87-35
ssh ip-172-31-89-182
ssh ip-172-31-93-20


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


# Cloudera Manager Prerequisties

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

ssh ip-172-31-91-58
ssh ip-172-31-89-46
ssh ip-172-31-87-35
ssh ip-172-31-89-182
ssh ip-172-31-93-20

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



