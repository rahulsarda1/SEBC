# Run the Hadoop pi program as user beltran

```sh
[root@ip-172-31-84-209 ec2-user]# su - beltran
[beltran@ip-172-31-84-209 ~]$ kinit
Password for beltran@RAHULSARDA1.TX:
[beltran@ip-172-31-84-209 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar pi 50 100
Number of Maps  = 50
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Wrote input for Map #10
Wrote input for Map #11
Wrote input for Map #12
Wrote input for Map #13
Wrote input for Map #14
Wrote input for Map #15
Wrote input for Map #16
Wrote input for Map #17
Wrote input for Map #18
Wrote input for Map #19
Wrote input for Map #20
Wrote input for Map #21
Wrote input for Map #22
Wrote input for Map #23
Wrote input for Map #24
Wrote input for Map #25
Wrote input for Map #26
Wrote input for Map #27
Wrote input for Map #28
Wrote input for Map #29
Wrote input for Map #30
Wrote input for Map #31
Wrote input for Map #32
Wrote input for Map #33
Wrote input for Map #34
Wrote input for Map #35
Wrote input for Map #36
Wrote input for Map #37
Wrote input for Map #38
Wrote input for Map #39
Wrote input for Map #40
Wrote input for Map #41
Wrote input for Map #42
Wrote input for Map #43
Wrote input for Map #44
Wrote input for Map #45
Wrote input for Map #46
Wrote input for Map #47
Wrote input for Map #48
Wrote input for Map #49
Starting Job
17/10/13 12:58:15 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-88-148.ec2.internal/172.31.88.148:8032
17/10/13 12:58:15 INFO hdfs.DFSClient: Created token for beltran: HDFS_DELEGATION_TOKEN owner=beltran@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507913895608, maxDate=1508518695608, sequenceNumber=1, masterKeyId=2 on 172.31.88.148:8020
17/10/13 12:58:15 INFO security.TokenCache: Got dt for hdfs://ip-172-31-88-148.ec2.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.88.148:8020, Ident: (token for beltran: HDFS_DELEGATION_TOKEN owner=beltran@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507913895608, maxDate=1508518695608, sequenceNumber=1, masterKeyId=2)
17/10/13 12:58:15 INFO input.FileInputFormat: Total input paths to process : 50
17/10/13 12:58:15 INFO mapreduce.JobSubmitter: number of splits:50
17/10/13 12:58:16 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507913680696_0001
17/10/13 12:58:16 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.88.148:8020, Ident: (token for beltran: HDFS_DELEGATION_TOKEN owner=beltran@RAHULSARDA1.TX, renewer=yarn, realUser=, issueDate=1507913895608, maxDate=1508518695608, sequenceNumber=1, masterKeyId=2)
17/10/13 12:58:17 INFO impl.YarnClientImpl: Submitted application application_1507913680696_0001
17/10/13 12:58:17 INFO mapreduce.Job: The url to track the job: http://ip-172-31-88-148.ec2.internal:8088/proxy/application_1507913680696_0001/
17/10/13 12:58:17 INFO mapreduce.Job: Running job: job_1507913680696_0001
17/10/13 12:58:27 INFO mapreduce.Job: Job job_1507913680696_0001 running in uber mode : false
17/10/13 12:58:27 INFO mapreduce.Job:  map 0% reduce 0%
17/10/13 12:58:32 INFO mapreduce.Job:  map 2% reduce 0%
17/10/13 12:58:36 INFO mapreduce.Job:  map 4% reduce 0%
17/10/13 12:58:38 INFO mapreduce.Job:  map 16% reduce 0%
17/10/13 12:58:40 INFO mapreduce.Job:  map 18% reduce 0%
17/10/13 12:58:43 INFO mapreduce.Job:  map 26% reduce 0%
17/10/13 12:58:44 INFO mapreduce.Job:  map 32% reduce 0%
17/10/13 12:58:48 INFO mapreduce.Job:  map 34% reduce 0%
17/10/13 12:58:49 INFO mapreduce.Job:  map 46% reduce 0%
17/10/13 12:58:53 INFO mapreduce.Job:  map 50% reduce 0%
17/10/13 12:58:54 INFO mapreduce.Job:  map 54% reduce 0%
17/10/13 12:58:55 INFO mapreduce.Job:  map 60% reduce 0%
17/10/13 12:58:57 INFO mapreduce.Job:  map 62% reduce 0%
17/10/13 12:58:58 INFO mapreduce.Job:  map 64% reduce 0%
17/10/13 12:58:59 INFO mapreduce.Job:  map 68% reduce 0%
17/10/13 12:59:00 INFO mapreduce.Job:  map 70% reduce 0%
17/10/13 12:59:01 INFO mapreduce.Job:  map 76% reduce 0%
17/10/13 12:59:03 INFO mapreduce.Job:  map 78% reduce 0%
17/10/13 12:59:04 INFO mapreduce.Job:  map 82% reduce 0%
17/10/13 12:59:05 INFO mapreduce.Job:  map 86% reduce 0%
17/10/13 12:59:07 INFO mapreduce.Job:  map 90% reduce 0%
17/10/13 12:59:08 INFO mapreduce.Job:  map 92% reduce 0%
17/10/13 12:59:09 INFO mapreduce.Job:  map 98% reduce 0%
17/10/13 12:59:10 INFO mapreduce.Job:  map 100% reduce 0%
17/10/13 12:59:12 INFO mapreduce.Job:  map 100% reduce 100%
17/10/13 12:59:12 INFO mapreduce.Job: Job job_1507913680696_0001 completed successfully
17/10/13 12:59:12 INFO mapreduce.Job: Counters: 49
File System Counters
FILE: Number of bytes read=262
FILE: Number of bytes written=6307893
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=14390
HDFS: Number of bytes written=215
HDFS: Number of read operations=203
HDFS: Number of large read operations=0
HDFS: Number of write operations=3
Job Counters
Launched map tasks=50
Launched reduce tasks=1
Data-local map tasks=50
Total time spent by all maps in occupied slots (ms)=235844
Total time spent by all reduces in occupied slots (ms)=3454
Total time spent by all map tasks (ms)=235844
Total time spent by all reduce tasks (ms)=3454
Total vcore-seconds taken by all map tasks=235844
Total vcore-seconds taken by all reduce tasks=3454
Total megabyte-seconds taken by all map tasks=241504256
Total megabyte-seconds taken by all reduce tasks=3536896
Map-Reduce Framework
Map input records=50
Map output records=100
Map output bytes=900
Map output materialized bytes=1700
Input split bytes=8490
Combine input records=0
Combine output records=0
Reduce input groups=2
Reduce shuffle bytes=1700
Reduce input records=100
Reduce output records=0
Spilled Records=200
Shuffled Maps =50
Failed Shuffles=0
Merged Map outputs=50
GC time elapsed (ms)=1359
CPU time spent (ms)=29490
Physical memory (bytes) snapshot=22605164544
Virtual memory (bytes) snapshot=80727879680
Total committed heap usage (bytes)=25694306304
Shuffle Errors
BAD_ID=0
CONNECTION=0
IO_ERROR=0
WRONG_LENGTH=0
WRONG_MAP=0
WRONG_REDUCE=0
File Input Format Counters
Bytes Read=5900
File Output Format Counters
Bytes Written=97
Job Finished in 57.349 seconds
Estimated value of Pi is 3.14160000000000000000
[beltran@ip-172-31-84-209 ~]$
```

