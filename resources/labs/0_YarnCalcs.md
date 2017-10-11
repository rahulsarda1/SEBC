
# Requirments for Impala CPU/Memory

CPU - Impala version 2.2 and higher uses the SSSE3 instruction set, which is included in newer processors.
Memory - 128 GB or more recommended, ideally 256 GB or more. If the intermediate results during query processing on a particular node exceed the amount of memory available to Impala on that node, the query writes temporary work data to disk, which can lead to long query times. Note that because the work is parallelized, and intermediate results for aggregate queries are typically smaller than the original data, Impala can query and join tables that are much larger than the memory available on an individual node.
Storage - DataNodes with 12 or more disks each. I/O speeds are often the limiting factor for disk performance with Impala. Ensure that you have sufficient disk space to store the data Impala will be querying.

# Why Workloads Matter
MapReduce job will either encounter a bottleneck reading data from disk or from the network (known as an IO-bound job) or in processing data (CPU-bound). An example of an IO-bound job is sorting, which requires very little processing (simple comparisons) and a lot of reading and writing to disk. An example of a CPU-bound job is classification, where some input data is processed in very complex ways to determine ontology.

Here are several more examples of IO-bound workloads:
Indexing
Grouping
Data importing and exporting
Data movement and transformation

Here are several more examples of CPU-bound workloads:
Clustering/Classification
Complex text mining
Natural-language processing
Feature extraction

# Physical Cores to Vcores Multiplier
Ratio is based on the expected number of concurrent threads per core.  Typical we use 1 for CPU intensive tasks up to 4 for standard I/O bound tasks.

Few useful guidleines
https://blog.cloudera.com/blog/2013/08/how-to-select-the-right-hardware-for-your-new-hadoop-cluster/ 
