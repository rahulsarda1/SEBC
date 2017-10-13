# The full teragen command and output

```sh
[jimenez@ip-172-31-88-148 root]$ time /usr/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapreduce.job.maps=8 -Ddfs.blocksize=67108864 -Dmapreduce.map.memory.mb=512 65536000  /user/jimenez/tgen
17/10/13 12:30:18 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-88-148.ec2.internal/172.31.88.148:8032
17/10/13 12:30:18 INFO terasort.TeraSort: Generating 65536000 using 8
17/10/13 12:30:18 INFO mapreduce.JobSubmitter: number of splits:8
17/10/13 12:30:19 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507910630223_0001
17/10/13 12:30:19 INFO impl.YarnClientImpl: Submitted application application_1507910630223_0001
17/10/13 12:30:19 INFO mapreduce.Job: The url to track the job: http://ip-172-31-88-148.ec2.internal:8088/proxy/application_1507910630223_0001/
17/10/13 12:30:19 INFO mapreduce.Job: Running job: job_1507910630223_0001
17/10/13 12:30:26 INFO mapreduce.Job: Job job_1507910630223_0001 running in uber mode : false
17/10/13 12:30:26 INFO mapreduce.Job:  map 0% reduce 0%
17/10/13 12:30:37 INFO mapreduce.Job:  map 5% reduce 0%
17/10/13 12:30:39 INFO mapreduce.Job:  map 19% reduce 0%
17/10/13 12:30:40 INFO mapreduce.Job:  map 20% reduce 0%
17/10/13 12:30:43 INFO mapreduce.Job:  map 27% reduce 0%
17/10/13 12:30:46 INFO mapreduce.Job:  map 31% reduce 0%
17/10/13 12:30:47 INFO mapreduce.Job:  map 32% reduce 0%
17/10/13 12:30:49 INFO mapreduce.Job:  map 36% reduce 0%
17/10/13 12:30:52 INFO mapreduce.Job:  map 41% reduce 0%
17/10/13 12:30:53 INFO mapreduce.Job:  map 42% reduce 0%
17/10/13 12:30:55 INFO mapreduce.Job:  map 45% reduce 0%
17/10/13 12:30:56 INFO mapreduce.Job:  map 46% reduce 0%
17/10/13 12:30:58 INFO mapreduce.Job:  map 50% reduce 0%
17/10/13 12:30:59 INFO mapreduce.Job:  map 51% reduce 0%
17/10/13 12:31:01 INFO mapreduce.Job:  map 55% reduce 0%
17/10/13 12:31:02 INFO mapreduce.Job:  map 56% reduce 0%
17/10/13 12:31:04 INFO mapreduce.Job:  map 59% reduce 0%
17/10/13 12:31:05 INFO mapreduce.Job:  map 60% reduce 0%
17/10/13 12:31:07 INFO mapreduce.Job:  map 63% reduce 0%
17/10/13 12:31:10 INFO mapreduce.Job:  map 68% reduce 0%
17/10/13 12:31:13 INFO mapreduce.Job:  map 72% reduce 0%
17/10/13 12:31:16 INFO mapreduce.Job:  map 76% reduce 0%
17/10/13 12:31:19 INFO mapreduce.Job:  map 80% reduce 0%
17/10/13 12:31:20 INFO mapreduce.Job:  map 81% reduce 0%
17/10/13 12:31:22 INFO mapreduce.Job:  map 84% reduce 0%
17/10/13 12:31:24 INFO mapreduce.Job:  map 85% reduce 0%
17/10/13 12:31:25 INFO mapreduce.Job:  map 87% reduce 0%
17/10/13 12:31:26 INFO mapreduce.Job:  map 88% reduce 0%
17/10/13 12:31:27 INFO mapreduce.Job:  map 89% reduce 0%
17/10/13 12:31:28 INFO mapreduce.Job:  map 90% reduce 0%
17/10/13 12:31:29 INFO mapreduce.Job:  map 91% reduce 0%
17/10/13 12:31:38 INFO mapreduce.Job:  map 95% reduce 0%
17/10/13 12:31:41 INFO mapreduce.Job:  map 98% reduce 0%
17/10/13 12:31:43 INFO mapreduce.Job:  map 100% reduce 0%
17/10/13 12:31:43 INFO mapreduce.Job: Job job_1507910630223_0001 completed successfully
17/10/13 12:31:43 INFO mapreduce.Job: Counters: 31
File System Counters
FILE: Number of bytes read=0
FILE: Number of bytes written=977616
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=682
HDFS: Number of bytes written=6553600000
HDFS: Number of read operations=32
HDFS: Number of large read operations=0
HDFS: Number of write operations=16
Job Counters
Launched map tasks=8
Other local map tasks=8
Total time spent by all maps in occupied slots (ms)=416699
Total time spent by all reduces in occupied slots (ms)=0
Total time spent by all map tasks (ms)=416699
Total vcore-seconds taken by all map tasks=416699
Total megabyte-seconds taken by all map tasks=426699776
Map-Reduce Framework
Map input records=65536000
Map output records=65536000
Input split bytes=682
Spilled Records=0
Failed Shuffles=0
Merged Map outputs=0
GC time elapsed (ms)=1470
CPU time spent (ms)=132710
Physical memory (bytes) snapshot=1404870656
Virtual memory (bytes) snapshot=9056669696
Total committed heap usage (bytes)=1773666304
org.apache.hadoop.examples.terasort.TeraGen$Counters
CHECKSUM=140750829423462787
File Input Format Counters
Bytes Read=0
File Output Format Counters
Bytes Written=6553600000

real    1m28.119s
user    0m6.219s
sys    0m0.269s
[jimenez@ip-172-31-88-148 root]$
```

# The result of the time command

```sh
real    1m28.119s
user    0m6.219s
sys    0m0.269s
```

# The command and output of hdfs dfs -ls /user/jimenez/tgen

```sh
[jimenez@ip-172-31-88-148 root]$ hdfs dfs -ls /user/jimenez/tgen
Found 9 items
-rw-r--r--   3 jimenez supergroup          0 2017-10-13 12:31 /user/jimenez/tgen/_SUCCESS
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00000
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00001
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00002
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00003
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00004
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00005
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00006
-rw-r--r--   3 jimenez supergroup  819200000 2017-10-13 12:31 /user/jimenez/tgen/part-m-00007
```

# The command and output of hadoop fsck -blocks /user/jimenez

```sh
[jimenez@ip-172-31-88-148 root]$ hadoop fsck -blocks /user/jimenez
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://ip-172-31-88-148.ec2.internal:50070
FSCK started by jimenez (auth:SIMPLE) from /172.31.88.148 for path /user/jimenez at Fri Oct 13 12:33:36 EDT 2017
.........Status: HEALTHY
Total size:    6553600000 B
Total dirs:    3
Total files:    9
Total symlinks:        0
Total blocks (validated):    104 (avg. block size 63015384 B)
Minimally replicated blocks:    104 (100.0 %)
Over-replicated blocks:    0 (0.0 %)
Under-replicated blocks:    0 (0.0 %)
Mis-replicated blocks:        0 (0.0 %)
Default replication factor:    3
Average block replication:    3.0
Corrupt blocks:        0
Missing replicas:        0 (0.0 %)
Number of data-nodes:        4
Number of racks:        1
FSCK ended at Fri Oct 13 12:33:36 EDT 2017 in 7 milliseconds


The filesystem under path '/user/jimenez' is HEALTHY
[jimenez@ip-172-31-88-148 root]$
```

