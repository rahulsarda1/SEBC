#!/bin/sh
# Confirm the path values given below correspond to your installation

HADOOP_MR=/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce
HADOOP_PATH=/opt/cloudera/parcels/CDH/bin

# Mark start of the loop
echo Testing loop started on `date`

# Mapper containers
for i in 8
do
   # Reducer containers
   for j in 1
   do
      # Container memory
      for k in 512 1024
      do
         # Set mapper JVM heap
         MAP_MB=`echo "($k*0.8)/1" | bc`

         # Set reducer JVM heap
         RED_MB=`echo "($k*0.8)/1" | bc`

        hdfs dfs -mkdir results/tg-10GB-${i}-${j}-${k}
        hdfs dfs -mkdir results/ts-10GB-${i}-${j}-${k}

        time $HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar teragen \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     10737418240 results/tg-10GB-${i}-${j}-${k} 1>tera_${i}_${j}_${k}.out 2>tera_${i}_${j}_${k}.err

        echo -Dmapreduce.job.maps=$i
        echo -Dmapreduce.map.memory.mb=$k
        echo -Dmapreduce.map.java.opts.max.heap=$MAP_MB

       time $HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar terasort \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.job.reduces=$j \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     -Dmapreduce.reduce.memory.mb=$k \
                     -Dmapreduce.reduce.java.opts.max.heap=$RED_MB \
                     results/tg-10GB-${i}-${j}-${k}  \
                     results/ts-10GB-${i}-${j}-${k} 1>>tera_${i}_${j}_${k}.out 2>>tera_${i}_${j}_${k}.err

        echo -Dmapreduce.job.maps=$i
        echo -Dmapreduce.job.reduces=$j
        echo -Dmapreduce.map.memory.mb=$k
        echo -Dmapreduce.map.java.opts.max.heap=$MAP_MB
        echo -Dmapreduce.reduce.memory.mb=$k
        echo -Dmapreduce.reduce.java.opts.max.heap=$RED_MB

        $HADOOP_PATH/hadoop fs -rm -r -skipTrash results/tg-10GB-${i}-${j}-${k}
        $HADOOP_PATH/hadoop fs -rm -r -skipTrash results/ts-10GB-${i}-${j}-${k}
      done
   done
done

echo Testing loop ended on `date`
