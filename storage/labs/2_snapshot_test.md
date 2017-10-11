## Create a precious directory in HDFS; copy the ZIP course file into it.

```sh
hdfs dfs -mkdir precious
hdfs dfs -put course.tar.gz /user/rahulsarda1/precious/

hdfs dfs -ls  /user/rahulsarda1/precious/

Found 1 items
-rw-r--r--   3 rahulsarda1 supergroup    3465760 2017-10-11 01:37 /user/rahulsarda1/precious/course.tar.gz
```

## Enable snapshots for precious

hdfs dfs -rmr /user/rahulsarda1/precious
hdfs dfs -rmr /user/rahulsarda1/precious/course.tar.gz


