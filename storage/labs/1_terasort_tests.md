# HDFS Lab: Test HDFS throughput

```
* EC2 Instance Details for quick use
* ssh -i "ClouderaRahul.pem" ec2-user@ec2-52-91-189-102.compute-1.amazonaws.com

ssh ip-172-31-90-35
ssh ip-172-31-95-78
ssh ip-172-31-86-146
ssh ip-172-31-87-246
ssh ip-172-31-89-87
```
## Create an end-user Linux account named with your GitHub handle
 - run following command on all nodes

```sh
userdel -r rahulsarda1
adduser rahulsarda1

passwd rahulsarda1
Changing password for user rahulsarda1.
New password:
Retype new password:
passwd: all authentication tokens updated successfully.

//password is - cloudera1

echo "rahulsarda1 ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

sudo su hdfs
hdfs dfs -mkdir /user/rahulsarda1
hdfs dfs -chown rahulsarda1 /user/rahulsarda1
hdfs dfs -chmod 777 /user/rahulsarda1
hdfs dfs -ls /user
exit
su rahulsarda1

cd /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce

```



# Teragen Example
sudo -u hdfs time hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Ddfs.block.size=33554432  -Dmapreduce.job.maps=4 100000000 /user/rahulsarda1/teragen

Argument 1: Number of 100 bytes rows ( 10,000,000,00 ), which is 100GB in this example.

Argument 2: Generated data will be dropped in the HDFS path entered

Argument 3: Block size

Argument 4: Number of map tasks

TeraGen will run map tasks to generate the data and will not run any reduce tasks. The default number of map task is defined by the "mapred.reduce.tasks=2" param. It's the only purpose here is to generate the 100GB of random data in the following format "10 bytes key | 2 bytes break | 32 bytes acsii/hex | 4 bytes break |  48 bytes filler | 4 bytes break | \r\n"

```sh
[rahulsarda1@ip-172-31-90-35 ~]$ sudo -u hdfs time hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Ddfs.block.size=33554432  -Dmapreduce.job.maps=4 1000000 /user/rahulsarda1/teragen
17/10/11 01:12:51 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-90-35.ec2.internal/172.31.90.35:8032
17/10/11 01:12:51 INFO terasort.TeraSort: Generating 1000000 using 4
17/10/11 01:12:51 INFO mapreduce.JobSubmitter: number of splits:4
17/10/11 01:12:51 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/11 01:12:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507691395559_0008
17/10/11 01:12:52 INFO impl.YarnClientImpl: Submitted application application_1507691395559_0008
17/10/11 01:12:52 INFO mapreduce.Job: The url to track the job: http://ip-172-31-90-35.ec2.internal:8088/proxy/application_1507691395559_0008/
17/10/11 01:12:52 INFO mapreduce.Job: Running job: job_1507691395559_0008
17/10/11 01:12:58 INFO mapreduce.Job: Job job_1507691395559_0008 running in uber mode : false
17/10/11 01:12:58 INFO mapreduce.Job:  map 0% reduce 0%
17/10/11 01:13:04 INFO mapreduce.Job:  map 25% reduce 0%
17/10/11 01:13:08 INFO mapreduce.Job:  map 100% reduce 0%
17/10/11 01:13:09 INFO mapreduce.Job: Job job_1507691395559_0008 completed successfully
17/10/11 01:13:09 INFO mapreduce.Job: Counters: 31
File System Counters
FILE: Number of bytes read=0
FILE: Number of bytes written=493092
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=337
HDFS: Number of bytes written=100000000
HDFS: Number of read operations=16
HDFS: Number of large read operations=0
HDFS: Number of write operations=8
Job Counters
Launched map tasks=4
Other local map tasks=4
Total time spent by all maps in occupied slots (ms)=29721
Total time spent by all reduces in occupied slots (ms)=0
Total time spent by all map tasks (ms)=29721
Total vcore-seconds taken by all map tasks=29721
Total megabyte-seconds taken by all map tasks=30434304
Map-Reduce Framework
Map input records=1000000
Map output records=1000000
Input split bytes=337
Spilled Records=0
Failed Shuffles=0
Merged Map outputs=0
GC time elapsed (ms)=269
CPU time spent (ms)=10950
Physical memory (bytes) snapshot=796987392
Virtual memory (bytes) snapshot=6340993024
Total committed heap usage (bytes)=1159725056
org.apache.hadoop.examples.terasort.TeraGen$Counters
CHECKSUM=2148987642402270
File Input Format Counters
Bytes Read=0
File Output Format Counters
Bytes Written=100000000
5.87user 0.27system 0:21.00elapsed 29%CPU (0avgtext+0avgdata 176052maxresident)k
0inputs+1816outputs (0major+59775minor)pagefaults 0swaps
[rahulsarda1@ip-172-31-90-35 ~]$
```

# Terasort
time sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/rahulsarda1/teragen /user/rahulsarda1/terasort
```sh
[rahulsarda1@ip-172-31-90-35 ~]$ time sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/rahulsarda1/teragen /user/rahulsarda1/terasort
17/10/11 01:21:04 INFO terasort.TeraSort: starting
17/10/11 01:21:06 INFO input.FileInputFormat: Total input paths to process : 4
Spent 136ms computing base-splits.
Spent 2ms computing TeraScheduler splits.
Computing input splits took 139ms
Sampling 4 splits of 4
Making 8 from 100000 sampled records
Computing parititions took 634ms
Spent 776ms computing partitions.
17/10/11 01:21:06 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-90-35.ec2.internal/172.31.90.35:8032
17/10/11 01:21:07 INFO mapreduce.JobSubmitter: number of splits:4
17/10/11 01:21:07 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507691395559_0010
17/10/11 01:21:07 INFO impl.YarnClientImpl: Submitted application application_1507691395559_0010
17/10/11 01:21:07 INFO mapreduce.Job: The url to track the job: http://ip-172-31-90-35.ec2.internal:8088/proxy/application_1507691395559_0010/
17/10/11 01:21:07 INFO mapreduce.Job: Running job: job_1507691395559_0010
17/10/11 01:21:13 INFO mapreduce.Job: Job job_1507691395559_0010 running in uber mode : false
17/10/11 01:21:13 INFO mapreduce.Job:  map 0% reduce 0%
17/10/11 01:21:20 INFO mapreduce.Job:  map 25% reduce 0%
17/10/11 01:21:24 INFO mapreduce.Job:  map 100% reduce 0%
17/10/11 01:21:34 INFO mapreduce.Job:  map 100% reduce 13%
17/10/11 01:21:35 INFO mapreduce.Job:  map 100% reduce 25%
17/10/11 01:21:37 INFO mapreduce.Job:  map 100% reduce 100%
17/10/11 01:21:38 INFO mapreduce.Job: Job job_1507691395559_0010 completed successfully
17/10/11 01:21:38 INFO mapreduce.Job: Counters: 50
File System Counters
FILE: Number of bytes read=43314301
FILE: Number of bytes written=88157398
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=100000572
HDFS: Number of bytes written=100000000
HDFS: Number of read operations=36
HDFS: Number of large read operations=0
HDFS: Number of write operations=16
Job Counters
Launched map tasks=4
Launched reduce tasks=8
Data-local map tasks=1
Rack-local map tasks=3
Total time spent by all maps in occupied slots (ms)=31962
Total time spent by all reduces in occupied slots (ms)=67822
Total time spent by all map tasks (ms)=31962
Total time spent by all reduce tasks (ms)=67822
Total vcore-seconds taken by all map tasks=31962
Total vcore-seconds taken by all reduce tasks=67822
Total megabyte-seconds taken by all map tasks=32729088
Total megabyte-seconds taken by all reduce tasks=69449728
Map-Reduce Framework
Map input records=1000000
Map output records=1000000
Map output bytes=102000000
Map output materialized bytes=43346929
Input split bytes=572
Combine input records=0
Combine output records=0
Reduce input groups=1000000
Reduce shuffle bytes=43346929
Reduce input records=1000000
Reduce output records=1000000
Spilled Records=2000000
Shuffled Maps =32
Failed Shuffles=0
Merged Map outputs=32
GC time elapsed (ms)=927
CPU time spent (ms)=42890
Physical memory (bytes) snapshot=3324305408
Virtual memory (bytes) snapshot=19116736512
Total committed heap usage (bytes)=4494721024
Shuffle Errors
BAD_ID=0
CONNECTION=0
IO_ERROR=0
WRONG_LENGTH=0
WRONG_MAP=0
WRONG_REDUCE=0
File Input Format Counters
Bytes Read=100000000
File Output Format Counters
Bytes Written=100000000
17/10/11 01:21:38 INFO terasort.TeraSort: done

real    0m34.521s
user    0m7.286s
sys    0m0.288s
```







