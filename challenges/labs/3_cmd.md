# List the command and output for ls /etc/yum.repos.d in challenges/labs/1_cm.md

```sh
[root@ip-172-31-88-148 ~]# ls /etc/yum.repos.d
cloudera-manager.repo  redhat.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhui-load-balancers.conf
```

# The command and output for hdfs dfs -ls /user

```sh
[root@ip-172-31-88-148 ~]# hdfs dfs -ls /user
Found 8 items
drwxrwxrwx   - jimenez     supergroup           0 2017-10-13 12:20 /user/beltran
drwxr-xr-x   - hdfs        supergroup           0 2017-10-13 12:15 /user/hdfs
drwxrwxrwx   - mapred      hadoop               0 2017-10-13 12:03 /user/history
drwxrwxr-t   - hive        hive                 0 2017-10-13 12:04 /user/hive
drwxrwxr-x   - hue         hue                  0 2017-10-13 12:15 /user/hue
drwxrwxrwx   - jimenez     supergroup           0 2017-10-13 12:20 /user/jimenez
drwxrwxr-x   - oozie       oozie                0 2017-10-13 12:05 /user/oozie
drwxr-xr-x   - rahulsarda1 rahulsarda1          0 2017-10-13 12:15 /user/rahulsarda1
```

# The command and output from the CM API call ../api/v5/hosts

```sh
[root@ip-172-31-88-148 ~]# curl -u 'admin:admin' -X GET "http://52.91.69.236:7180/api/v5/hosts"
{
"items" : [ {
"hostId" : "d1e54e3f-2a2e-4118-9ee7-c69a50e0c7ed",
"ipAddress" : "172.31.82.13",
"hostname" : "ip-172-31-82-13.ec2.internal",
"rackId" : "/default",
"hostUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/hostRedirect/d1e54e3f-2a2e-4118-9ee7-c69a50e0c7ed",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"commissionState" : "COMMISSIONED",
"numCores" : 4,
"totalPhysMemBytes" : 15332438016
}, {
"hostId" : "44046a02-c6eb-453f-8a7a-68705f5f4b51",
"ipAddress" : "172.31.83.106",
"hostname" : "ip-172-31-83-106.ec2.internal",
"rackId" : "/default",
"hostUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/hostRedirect/44046a02-c6eb-453f-8a7a-68705f5f4b51",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"commissionState" : "COMMISSIONED",
"numCores" : 4,
"totalPhysMemBytes" : 15332438016
}, {
"hostId" : "60cc9085-e47d-4c02-a9db-4630dd469271",
"ipAddress" : "172.31.84.209",
"hostname" : "ip-172-31-84-209.ec2.internal",
"rackId" : "/default",
"hostUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/hostRedirect/60cc9085-e47d-4c02-a9db-4630dd469271",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"commissionState" : "COMMISSIONED",
"numCores" : 4,
"totalPhysMemBytes" : 15332438016
}, {
"hostId" : "5a418e01-e2a8-40f5-b94c-523640fd3d79",
"ipAddress" : "172.31.88.148",
"hostname" : "ip-172-31-88-148.ec2.internal",
"rackId" : "/default",
"hostUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/hostRedirect/5a418e01-e2a8-40f5-b94c-523640fd3d79",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"commissionState" : "COMMISSIONED",
"numCores" : 4,
"totalPhysMemBytes" : 15332438016
}, {
"hostId" : "6c62244a-fd6a-46ce-b909-83e673b4e320",
"ipAddress" : "172.31.95.176",
"hostname" : "ip-172-31-95-176.ec2.internal",
"rackId" : "/default",
"hostUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/hostRedirect/6c62244a-fd6a-46ce-b909-83e673b4e320",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"commissionState" : "COMMISSIONED",
"numCores" : 4,
"totalPhysMemBytes" : 15332438016
} ]
}[root@ip-172-31-88-148 ~]#
```

# The command and output from the CM API call ../api/v8/clusters/<githubName>/services

```sh
[root@ip-172-31-88-148 ~]# curl -u 'admin:admin' -X GET "http://52.91.69.236:7180/api/v11/clusters/rahulsarda1/services"
{
"items" : [ {
"name" : "zookeeper",
"type" : "ZOOKEEPER",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/zookeeper",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/zookeeper/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "ZOOKEEPER_CANARY_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "ZOOKEEPER_SERVERS_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "ZooKeeper",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "oozie",
"type" : "OOZIE",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/oozie",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/oozie/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "Oozie",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "hue",
"type" : "HUE",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hue",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hue/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "HUE_HUE_SERVERS_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HUE_LOAD_BALANCER_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "Hue",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "hdfs",
"type" : "HDFS",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hdfs",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hdfs/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_CANARY_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_DATA_NODES_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_FREE_SPACE_REMAINING",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_HA_NAMENODE_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_MISSING_BLOCKS",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HDFS_UNDER_REPLICATED_BLOCKS",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "HDFS",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "yarn",
"type" : "YARN",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/yarn",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/yarn/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "YARN_JOBHISTORY_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "YARN_NODE_MANAGERS_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "YARN_RESOURCEMANAGERS_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "YARN_USAGE_AGGREGATION_HEALTH",
"summary" : "DISABLED",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "YARN (MR2 Included)",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "hbase",
"type" : "HBASE",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hbase",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hbase/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "HBASE_MASTER_HEALTH",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HBASE_REGION_SERVERS_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "HBase",
"entityStatus" : "GOOD_HEALTH"
}, {
"name" : "hive",
"type" : "HIVE",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hive",
"roleInstancesUrl" : "http://ip-172-31-88-148.ec2.internal:7180/cmf/serviceRedirect/hive/instances",
"serviceState" : "STARTED",
"healthSummary" : "GOOD",
"healthChecks" : [ {
"name" : "HIVE_HIVEMETASTORES_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
}, {
"name" : "HIVE_HIVESERVER2S_HEALTHY",
"summary" : "GOOD",
"suppressed" : false
} ],
"configStalenessStatus" : "FRESH",
"clientConfigStalenessStatus" : "FRESH",
"maintenanceMode" : false,
"maintenanceOwners" : [ ],
"displayName" : "Hive",
"entityStatus" : "GOOD_HEALTH"
} ]
}[root@ip-172-31-88-148 ~]#
```

