# Run the terasort program as user jimenez with the output target /user/jimenez/tsort

```sh
[jimenez@ip-172-31-84-209 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_2800
Default principal: jimenez@RAHULSARDA1.TX

Valid starting       Expires              Service principal
10/13/2017 13:00:46  10/14/2017 13:00:46  krbtgt/RAHULSARDA1.TX@RAHULSARDA1.TX
renew until 10/20/2017 13:00:46
[jimenez@ip-172-31-84-209 ~]$ /usr/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/jimenez/tgen/ /user/jimenez/tsort/
17/10/13 13:01:32 INFO terasort.TeraSort: starting
17/10/13 13:01:33 INFO hdfs.DFSClient: Created token for jimenez: HDFS_DELEGATION_TOKEN owner=jimenez@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507914093911, maxDate=1508518893911, sequenceNumber=2, masterKeyId=2 on 172.31.88.148:8020
17/10/13 13:01:33 INFO security.TokenCache: Got dt for hdfs://ip-172-31-88-148.ec2.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.88.148:8020, Ident: (token for jimenez: HDFS_DELEGATION_TOKEN owner=jimenez@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507914093911, maxDate=1508518893911, sequenceNumber=2, masterKeyId=2)
17/10/13 13:01:34 INFO input.FileInputFormat: Total input paths to process : 8
Spent 304ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 309ms
Sampling 10 splits of 104
Making 8 from 100000 sampled records
Computing parititions took 769ms
Spent 1080ms computing partitions.
17/10/13 13:01:34 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-88-148.ec2.internal/172.31.88.148:8032
17/10/13 13:01:35 INFO mapreduce.JobSubmitter: number of splits:104
17/10/13 13:01:35 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507913680696_0002
17/10/13 13:01:35 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.88.148:8020, Ident: (token for jimenez: HDFS_DELEGATION_TOKEN owner=jimenez@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507914093911, maxDate=1508518893911, sequenceNumber=2, masterKeyId=2)
17/10/13 13:01:35 INFO impl.YarnClientImpl: Submitted application application_1507913680696_0002
17/10/13 13:01:35 INFO mapreduce.Job: The url to track the job: http://ip-172-31-88-148.ec2.internal:8088/proxy/application_1507913680696_0002/
17/10/13 13:01:35 INFO mapreduce.Job: Running job: job_1507913680696_0002
17/10/13 13:01:44 INFO mapreduce.Job: Job job_1507913680696_0002 running in uber mode : false
17/10/13 13:01:44 INFO mapreduce.Job:  map 0% reduce 0%
17/10/13 13:01:52 INFO mapreduce.Job:  map 1% reduce 0%
17/10/13 13:01:57 INFO mapreduce.Job:  map 7% reduce 0%
17/10/13 13:01:58 INFO mapreduce.Job:  map 8% reduce 0%
17/10/13 13:02:05 INFO mapreduce.Job:  map 13% reduce 0%
17/10/13 13:02:06 INFO mapreduce.Job:  map 14% reduce 0%
17/10/13 13:02:13 INFO mapreduce.Job:  map 16% reduce 0%
17/10/13 13:02:14 INFO mapreduce.Job:  map 19% reduce 0%
17/10/13 13:02:15 INFO mapreduce.Job:  map 21% reduce 0%
17/10/13 13:02:19 INFO mapreduce.Job:  map 22% reduce 0%
17/10/13 13:02:22 INFO mapreduce.Job:  map 25% reduce 0%
17/10/13 13:02:23 INFO mapreduce.Job:  map 28% reduce 0%
17/10/13 13:02:26 INFO mapreduce.Job:  map 29% reduce 0%
17/10/13 13:02:30 INFO mapreduce.Job:  map 32% reduce 0%
17/10/13 13:02:31 INFO mapreduce.Job:  map 35% reduce 0%
17/10/13 13:02:33 INFO mapreduce.Job:  map 36% reduce 0%
17/10/13 13:02:38 INFO mapreduce.Job:  map 38% reduce 0%
17/10/13 13:02:39 INFO mapreduce.Job:  map 41% reduce 0%
17/10/13 13:02:40 INFO mapreduce.Job:  map 42% reduce 0%
17/10/13 13:02:46 INFO mapreduce.Job:  map 44% reduce 0%
17/10/13 13:02:47 INFO mapreduce.Job:  map 49% reduce 0%
17/10/13 13:02:54 INFO mapreduce.Job:  map 52% reduce 0%
17/10/13 13:02:55 INFO mapreduce.Job:  map 54% reduce 0%
17/10/13 13:02:56 INFO mapreduce.Job:  map 56% reduce 0%
17/10/13 13:03:01 INFO mapreduce.Job:  map 57% reduce 0%
17/10/13 13:03:02 INFO mapreduce.Job:  map 59% reduce 0%
17/10/13 13:03:03 INFO mapreduce.Job:  map 61% reduce 0%
17/10/13 13:03:05 INFO mapreduce.Job:  map 63% reduce 0%
17/10/13 13:03:10 INFO mapreduce.Job:  map 65% reduce 0%
17/10/13 13:03:11 INFO mapreduce.Job:  map 67% reduce 0%
17/10/13 13:03:14 INFO mapreduce.Job:  map 69% reduce 0%
17/10/13 13:03:15 INFO mapreduce.Job:  map 70% reduce 0%
17/10/13 13:03:18 INFO mapreduce.Job:  map 72% reduce 0%
17/10/13 13:03:19 INFO mapreduce.Job:  map 74% reduce 0%
17/10/13 13:03:22 INFO mapreduce.Job:  map 77% reduce 0%
17/10/13 13:03:26 INFO mapreduce.Job:  map 79% reduce 0%
17/10/13 13:03:27 INFO mapreduce.Job:  map 81% reduce 0%
17/10/13 13:03:29 INFO mapreduce.Job:  map 82% reduce 0%
17/10/13 13:03:30 INFO mapreduce.Job:  map 83% reduce 0%
17/10/13 13:03:31 INFO mapreduce.Job:  map 84% reduce 0%
17/10/13 13:03:33 INFO mapreduce.Job:  map 85% reduce 0%
17/10/13 13:03:34 INFO mapreduce.Job:  map 86% reduce 0%
17/10/13 13:03:35 INFO mapreduce.Job:  map 88% reduce 0%
17/10/13 13:03:38 INFO mapreduce.Job:  map 89% reduce 0%
17/10/13 13:03:40 INFO mapreduce.Job:  map 90% reduce 0%
17/10/13 13:03:41 INFO mapreduce.Job:  map 90% reduce 4%
17/10/13 13:03:42 INFO mapreduce.Job:  map 91% reduce 4%
17/10/13 13:03:46 INFO mapreduce.Job:  map 92% reduce 15%
17/10/13 13:03:49 INFO mapreduce.Job:  map 92% reduce 19%
17/10/13 13:03:50 INFO mapreduce.Job:  map 93% reduce 19%
17/10/13 13:03:52 INFO mapreduce.Job:  map 94% reduce 19%
17/10/13 13:03:55 INFO mapreduce.Job:  map 94% reduce 20%
17/10/13 13:03:57 INFO mapreduce.Job:  map 96% reduce 20%
17/10/13 13:04:02 INFO mapreduce.Job:  map 97% reduce 20%
17/10/13 13:04:03 INFO mapreduce.Job:  map 98% reduce 20%
17/10/13 13:04:07 INFO mapreduce.Job:  map 99% reduce 21%
17/10/13 13:04:08 INFO mapreduce.Job:  map 100% reduce 21%
17/10/13 13:04:10 INFO mapreduce.Job:  map 100% reduce 33%
17/10/13 13:04:11 INFO mapreduce.Job:  map 100% reduce 38%
17/10/13 13:04:13 INFO mapreduce.Job:  map 100% reduce 42%
17/10/13 13:04:14 INFO mapreduce.Job:  map 100% reduce 44%
17/10/13 13:04:15 INFO mapreduce.Job:  map 100% reduce 46%
17/10/13 13:04:16 INFO mapreduce.Job:  map 100% reduce 47%
17/10/13 13:04:17 INFO mapreduce.Job:  map 100% reduce 50%
17/10/13 13:04:18 INFO mapreduce.Job:  map 100% reduce 55%
17/10/13 13:04:19 INFO mapreduce.Job:  map 100% reduce 57%
17/10/13 13:04:20 INFO mapreduce.Job:  map 100% reduce 65%
17/10/13 13:04:22 INFO mapreduce.Job:  map 100% reduce 68%
17/10/13 13:04:23 INFO mapreduce.Job:  map 100% reduce 70%
17/10/13 13:04:24 INFO mapreduce.Job:  map 100% reduce 75%
17/10/13 13:04:26 INFO mapreduce.Job:  map 100% reduce 80%
17/10/13 13:04:27 INFO mapreduce.Job:  map 100% reduce 81%
17/10/13 13:04:29 INFO mapreduce.Job:  map 100% reduce 83%
17/10/13 13:04:30 INFO mapreduce.Job:  map 100% reduce 88%
17/10/13 13:04:32 INFO mapreduce.Job:  map 100% reduce 90%
17/10/13 13:04:33 INFO mapreduce.Job:  map 100% reduce 96%
17/10/13 13:04:36 INFO mapreduce.Job:  map 100% reduce 97%
17/10/13 13:04:39 INFO mapreduce.Job:  map 100% reduce 99%
17/10/13 13:04:42 INFO mapreduce.Job:  map 100% reduce 100%
17/10/13 13:04:42 INFO mapreduce.Job: Job job_1507913680696_0002 completed successfully
17/10/13 13:04:42 INFO mapreduce.Job: Counters: 49
File System Counters
FILE: Number of bytes read=2912339530
FILE: Number of bytes written=5778211544
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=6553614248
HDFS: Number of bytes written=6553600000
HDFS: Number of read operations=336
HDFS: Number of large read operations=0
HDFS: Number of write operations=16
Job Counters
Launched map tasks=104
Launched reduce tasks=8
Data-local map tasks=104
Total time spent by all maps in occupied slots (ms)=731677
Total time spent by all reduces in occupied slots (ms)=299717
Total time spent by all map tasks (ms)=731677
Total time spent by all reduce tasks (ms)=299717
Total vcore-seconds taken by all map tasks=731677
Total vcore-seconds taken by all reduce tasks=299717
Total megabyte-seconds taken by all map tasks=749237248
Total megabyte-seconds taken by all reduce tasks=306910208
Map-Reduce Framework
Map input records=65536000
Map output records=65536000
Map output bytes=6684672000
Map output materialized bytes=2851934348
Input split bytes=14248
Combine input records=0
Combine output records=0
Reduce input groups=65536000
Reduce shuffle bytes=2851934348
Reduce input records=65536000
Reduce output records=65536000
Spilled Records=131072000
Shuffled Maps =832
Failed Shuffles=0
Merged Map outputs=832
GC time elapsed (ms)=11763
CPU time spent (ms)=668120
Physical memory (bytes) snapshot=58483077120
Virtual memory (bytes) snapshot=177160925184
Total committed heap usage (bytes)=64401965056
Shuffle Errors
BAD_ID=0
CONNECTION=0
IO_ERROR=0
WRONG_LENGTH=0
WRONG_MAP=0
WRONG_REDUCE=0
File Input Format Counters
Bytes Read=6553600000
File Output Format Counters
Bytes Written=6553600000
17/10/13 13:04:42 INFO terasort.TeraSort: done
[jimenez@ip-172-31-84-209 ~]$ 
```

