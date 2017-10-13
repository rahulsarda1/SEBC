
# Authenticate using Linux users/groups
```sh
[root@ip-172-31-90-163 ec2-user]# for i in `cat ~/hosts`; do echo $i; ssh $i "cat /etc/group | grep hadoop"; done
ip-172-31-90-163.ec2.internal
hadoop:x:991:hdfs,mapred,yarn
ip-172-31-90-157.ec2.internal
hadoop:x:991:hdfs,mapred,yarn
ip-172-31-91-100.ec2.internal
hadoop:x:991:hdfs,mapred,yarn
ip-172-31-89-10.ec2.internal
hadoop:x:991:hdfs,mapred,yarn
ip-172-31-80-39.ec2.internal
hadoop:x:991:hdfs,mapred,yarn
[root@ip-172-31-90-163 ec2-user]# export HUE_DATABASE_PASSWORD=mariadb
[root@ip-172-31-90-163 ec2-user]# export HUE_IGNORE_PASSWORD_SCRIPT_ERRORS=1
[root@ip-172-31-90-163 ec2-user]# export JAVA_HOME=/usr/java/latest
[root@ip-172-31-90-163 ec2-user]# export HUE_CONF_DIR="/var/run/cloudera-scm-agent/process/`ls -alrt /var/run/cloudera-scm-agent/process | grep HUE | tail -1 | awk '{print $9}'`"
[root@ip-172-31-90-163 ec2-user]# /opt/cloudera/parcels/CDH/lib/hue/build/env/bin/hue useradmin_sync_with_unix
[12/Oct/2017 13:14:10 +0000] settings     DEBUG    DESKTOP_DB_TEST_NAME SET: /opt/cloudera/parcels/CDH-5.13.0-1.cdh5.13.0.p0.29/lib/hue/desktop/desktop-test.db
[12/Oct/2017 13:14:10 +0000] settings     DEBUG    DESKTOP_DB_TEST_USER SET: hue_test
[12/Oct/2017 10:14:11 +0000] __init__     INFO     Couldn't import snappy. Support for snappy compression disabled.
[12/Oct/2017 10:14:11 +0000] decorators   INFO     AXES: BEGIN LOG
[12/Oct/2017 10:14:11 +0000] decorators   INFO     Using django-axes 1.5.0
[12/Oct/2017 10:14:11 +0000] views        INFO     Created group sqoop
[12/Oct/2017 10:14:11 +0000] views        INFO     Created group hive
[12/Oct/2017 10:14:11 +0000] views        INFO     Created group hadoop
[12/Oct/2017 10:14:11 +0000] views        INFO     Created group sentryadmin
[12/Oct/2017 10:14:11 +0000] views        INFO     Created group llama
[12/Oct/2017 10:14:11 +0000] views        INFO     Synced user httpfs from Unix
[12/Oct/2017 10:14:11 +0000] views        INFO     Synced user rahulsarda1 from Unix
[12/Oct/2017 10:14:11 +0000] views        INFO     Synced user george from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user hdfs from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user kms from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user ferdinand from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user mapred from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user llama from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user ec2-user from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user yarn from Unix
[12/Oct/2017 10:14:12 +0000] views        INFO     Synced user impala from Unix
[root@ip-172-31-90-163 ec2-user]#
```




