
# List the cloud provider you are using
```sh
    AWS US East (N. Virginia)
```

# List your instances by IP address and DNS name (don't use /etc/hosts for this)

# INTERNAL IP ADDRESS, DNS NAME,
```sh
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-83-106.ec2.internal
ip-172-31-82-13.ec2.internal
```

```sh
ec2-34-203-243-182.compute-1.amazonaws.com
ec2-52-91-69-236.compute-1.amazonaws.com
ec2-34-207-162-78.compute-1.amazonaws.com
ec2-52-207-186-139.compute-1.amazonaws.com
ec2-54-165-121-153.compute-1.amazonaws.com
```
# Public Address
```sh
34.203.243.182
52.91.69.236
34.207.162.78
52.207.186.139
54.165.121.153
```

# List the Linux release you are using
```sh
Red Hat Linux Version 7.2. - RHEL-7.2_HVM_GA-20151112-x86_64-1-Hourly2-GP2 (ami-2051294a)
Red Hat Enterprise Linux version 7.2 (HVM), EBS General Purpose (SSD) Volume Type
```

# List the file system capacity for the first node

```sh
[root@ip-172-31-84-209 ec2-user]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  1.2G   29G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000
```

# List the command and output for yum repolist enabled

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "yum repolist enabled"; done
ip-172-31-84-209.ec2.internal
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 17,255
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 17,489
ip-172-31-88-148.ec2.internal
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 17,255
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 17,489
ip-172-31-95-176.ec2.internal
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 17,255
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 17,489
ip-172-31-82-13.ec2.internal
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 17,255
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 17,489
ip-172-31-83-106.ec2.internal
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 17,255
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 17,489
[root@ip-172-31-84-209 ec2-user]#
```
## Add user with UID to all nodes

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "useradd -u 2800 jimenez";done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal
```

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "useradd -u 2900 beltran";done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal
```

## Create Group and Add user to that group

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "groupadd astros"; done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal

[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "groupadd rangers"; done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal
```

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "usermod -G astros jimenez"; done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal

[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "usermod -G rangers beltran"; done
ip-172-31-84-209.ec2.internal
ip-172-31-88-148.ec2.internal
ip-172-31-95-176.ec2.internal
ip-172-31-82-13.ec2.internal
ip-172-31-83-106.ec2.internal
```

## List the /etc/passwd entries

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "cat /etc/passwd | grep jimenez"; done
ip-172-31-84-209.ec2.internal
jimenez:x:2800:2800::/home/jimenez:/bin/bash
ip-172-31-88-148.ec2.internal
jimenez:x:2800:2800::/home/jimenez:/bin/bash
ip-172-31-95-176.ec2.internal
jimenez:x:2800:2800::/home/jimenez:/bin/bash
ip-172-31-82-13.ec2.internal
jimenez:x:2800:2800::/home/jimenez:/bin/bash
ip-172-31-83-106.ec2.internal
jimenez:x:2800:2800::/home/jimenez:/bin/bash
```

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "cat /etc/passwd | grep beltran"; done
ip-172-31-84-209.ec2.internal
beltran:x:2900:2900::/home/beltran:/bin/bash
ip-172-31-88-148.ec2.internal
beltran:x:2900:2900::/home/beltran:/bin/bash
ip-172-31-95-176.ec2.internal
beltran:x:2900:2900::/home/beltran:/bin/bash
ip-172-31-82-13.ec2.internal
beltran:x:2900:2900::/home/beltran:/bin/bash
ip-172-31-83-106.ec2.internal
beltran:x:2900:2900::/home/beltran:/bin/bash
[root@ip-172-31-84-209 ec2-user]#

```

## List the /etc/group entries for pictures and bridges in your setup file

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "cat /etc/group | grep astros"; done
ip-172-31-84-209.ec2.internal
astros:x:2901:jimenez
ip-172-31-88-148.ec2.internal
astros:x:2901:jimenez
ip-172-31-95-176.ec2.internal
astros:x:2901:jimenez
ip-172-31-82-13.ec2.internal
astros:x:2901:jimenez
ip-172-31-83-106.ec2.internal
astros:x:2901:jimenez
```

```sh
[root@ip-172-31-84-209 ec2-user]# for i in `cat hosts`; do echo $i; ssh $i "cat /etc/group | grep rangers"; done
ip-172-31-84-209.ec2.internal
rangers:x:2902:beltran
ip-172-31-88-148.ec2.internal
rangers:x:2902:beltran
ip-172-31-95-176.ec2.internal
rangers:x:2902:beltran
ip-172-31-82-13.ec2.internal
rangers:x:2902:beltran
ip-172-31-83-106.ec2.internal
rangers:x:2902:beltran
[root@ip-172-31-84-209 ec2-user]#
```






