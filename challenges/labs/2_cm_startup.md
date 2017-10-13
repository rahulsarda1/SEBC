# The line(s) that contain the phrase "Started Jetty server"

```sh
[root@ip-172-31-88-148 ~]# grep "Started Jetty server" /var/log/cloudera-scm-server/cloudera-scm-server.log
2017-10-13 11:25:48,942 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```
cat /var/log/cloudera-scm-server/cloudera-scm-server.log | grep -B 2 -A 2 "Started Jetty server"

# The first line of the server log

cat /var/log/cloudera-scm-server/cloudera-scm-server.log | head -1

```sh
[root@ip-172-31-88-148 ~]# cat /var/log/cloudera-scm-server/cloudera-scm-server.log | head -1
2017-10-13 11:24:36,432 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.13.0 (#55 built by jenkins on 20171002-1719 git: bd657e597e6743c458ee2c9aabe808b7c972981c)
```
