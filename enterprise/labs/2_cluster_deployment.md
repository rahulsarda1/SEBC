# Browse or use curl on the endpoint ./api/v2/cm/deployment

## http command
```sh
http://52.91.189.102:7180/api/v2/cm/deployment
```
## Curl Command
```sh
curl -u 'admin:admin' http://52.91.189.102:7180/api/v2/cm/deployment
```
## Result

```sh
{
"timestamp" : "2017-10-11T15:52:49.321Z",
"clusters" : [ {
"name" : "Cluster 1",
"version" : "CDH5",
"services" : [ {
"name" : "zookeeper",
"type" : "ZOOKEEPER",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "SERVER",
"items" : [ {
"name" : "zookeeper_server_java_heapsize",
"value" : "593494016"
} ]
} ],
"items" : [ ]
},
"roles" : [ {
"name" : "zookeeper-SERVER-186261d19970f21ff6b566a28b59abf7",
"type" : "SERVER",
"hostRef" : {
"hostId" : "i-096dde2d24aee520b"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "9yof0bxidx058xh5uuoin5nz"
}, {
"name" : "serverId",
"value" : "3"
} ]
}
}, {
"name" : "zookeeper-SERVER-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "SERVER",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "5w116k9gvk1kxkefcsogs82ij"
}, {
"name" : "serverId",
"value" : "2"
} ]
}
}, {
"name" : "zookeeper-SERVER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "SERVER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "4gt2xs7nkv0zqooudxowk4q40"
}, {
"name" : "serverId",
"value" : "1"
} ]
}
} ],
"displayName" : "ZooKeeper"
}, {
"name" : "oozie",
"type" : "OOZIE",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "OOZIE_SERVER",
"items" : [ {
"name" : "oozie_database_host",
"value" : "ip-172-31-90-35.ec2.internal"
}, {
"name" : "oozie_database_password",
"value" : "mariadb"
}, {
"name" : "oozie_database_type",
"value" : "mysql"
}, {
"name" : "oozie_database_user",
"value" : "mariadbuser"
}, {
"name" : "oozie_java_heapsize",
"value" : "593494016"
} ]
} ],
"items" : [ {
"name" : "hive_service",
"value" : "hive"
}, {
"name" : "mapreduce_yarn_service",
"value" : "yarn"
}, {
"name" : "zookeeper_service",
"value" : "zookeeper"
} ]
},
"roles" : [ {
"name" : "oozie-OOZIE_SERVER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "OOZIE_SERVER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "663aqjv9iafl8873euch15qh0"
} ]
}
} ],
"displayName" : "Oozie"
}, {
"name" : "hue",
"type" : "HUE",
"config" : {
"roleTypeConfigs" : [ ],
"items" : [ {
"name" : "database_host",
"value" : "ip-172-31-90-35.ec2.internal"
}, {
"name" : "database_password",
"value" : "mariadb"
}, {
"name" : "database_type",
"value" : "mysql"
}, {
"name" : "database_user",
"value" : "mariadbuser"
}, {
"name" : "hive_service",
"value" : "hive"
}, {
"name" : "hue_webhdfs",
"value" : "hdfs-NAMENODE-bafb4828c9bbc315072f6c52193b5f45"
}, {
"name" : "oozie_service",
"value" : "oozie"
}, {
"name" : "zookeeper_service",
"value" : "zookeeper"
} ]
},
"roles" : [ {
"name" : "hue-HUE_SERVER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "HUE_SERVER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "a8v9gqo2io88t4uzf32seywkx"
}, {
"name" : "secret_key",
"value" : "liXibkqU0IGwxdW9yngkQtBTks9bYE"
} ]
}
} ],
"displayName" : "Hue"
}, {
"name" : "hdfs",
"type" : "HDFS",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "BALANCER",
"items" : [ {
"name" : "balancer_java_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "DATANODE",
"items" : [ {
"name" : "datanode_java_heapsize",
"value" : "1073741824"
}, {
"name" : "dfs_data_dir_list",
"value" : "/dfs/dn"
}, {
"name" : "dfs_datanode_du_reserved",
"value" : "3219965132"
}, {
"name" : "dfs_datanode_max_locked_memory",
"value" : "4294967296"
}, {
"name" : "rm_cpu_shares",
"value" : "400"
}, {
"name" : "rm_io_weight",
"value" : "200"
} ]
}, {
"roleType" : "GATEWAY",
"items" : [ {
"name" : "dfs_client_use_trash",
"value" : "true"
} ]
}, {
"roleType" : "JOURNALNODE",
"items" : [ {
"name" : "dfs_journalnode_edits_dir",
"value" : "/data/dfs/journalentry"
} ]
}, {
"roleType" : "NAMENODE",
"items" : [ {
"name" : "dfs_name_dir_list",
"value" : "/dfs/nn"
}, {
"name" : "dfs_namenode_servicerpc_address",
"value" : "8022"
}, {
"name" : "namenode_java_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "SECONDARYNAMENODE",
"items" : [ {
"name" : "fs_checkpoint_dir_list",
"value" : "/dfs/snn"
}, {
"name" : "secondary_namenode_java_heapsize",
"value" : "593494016"
} ]
} ],
"items" : [ {
"name" : "dfs_ha_fencing_cloudera_manager_secret_key",
"value" : "rSPIuCSkuGkpaw4TRKTEj9vdFQNmRg"
}, {
"name" : "dfs_ha_fencing_methods",
"value" : "shell(true)"
}, {
"name" : "fc_authorization_secret_key",
"value" : "flRnN79rS0SAAhnr9vaZkzaKx4SIus"
}, {
"name" : "http_auth_signature_secret",
"value" : "xzm5tG2fdtkeH1ZZ3lAsGRyVOyIn8C"
}, {
"name" : "rm_dirty",
"value" : "false"
}, {
"name" : "rm_last_allocation_percentage",
"value" : "20"
}, {
"name" : "zookeeper_service",
"value" : "zookeeper"
} ]
},
"roles" : [ {
"name" : "hdfs-BALANCER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "BALANCER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hdfs-DATANODE-186261d19970f21ff6b566a28b59abf7",
"type" : "DATANODE",
"hostRef" : {
"hostId" : "i-096dde2d24aee520b"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "906qghd2dzu1eocw53b5qrkbm"
} ]
}
}, {
"name" : "hdfs-DATANODE-28d425e2b5cce716b08c2b8cb100de68",
"type" : "DATANODE",
"hostRef" : {
"hostId" : "i-0d83575d8d57c4233"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "5mt22gjgawh3z4ragt7562ce0"
} ]
}
}, {
"name" : "hdfs-DATANODE-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "DATANODE",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "2s4szw46bv9u5zwv4t0nqngr1"
} ]
}
}, {
"name" : "hdfs-DATANODE-bfd01a4bc9574e3d724decaa1b03ab6e",
"type" : "DATANODE",
"hostRef" : {
"hostId" : "i-06f2256b7d2e0fd5a"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "8ahixkimw897oh9f2ytocqerc"
} ]
}
}, {
"name" : "hdfs-FAILOVERCONTROLLER-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "FAILOVERCONTROLLER",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "42exjzon0015s0kcya6l4ogru"
} ]
}
}, {
"name" : "hdfs-FAILOVERCONTROLLER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "FAILOVERCONTROLLER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "5i5iubdwbpqf7dievgr1i15cq"
} ]
}
}, {
"name" : "hdfs-JOURNALNODE-186261d19970f21ff6b566a28b59abf7",
"type" : "JOURNALNODE",
"hostRef" : {
"hostId" : "i-096dde2d24aee520b"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "5nhdns44n8zzrfqe10sqmf5ja"
} ]
}
}, {
"name" : "hdfs-JOURNALNODE-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "JOURNALNODE",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "8sk0chfkdbswgut6kdpxkotqk"
} ]
}
}, {
"name" : "hdfs-JOURNALNODE-bafb4828c9bbc315072f6c52193b5f45",
"type" : "JOURNALNODE",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "7og3cgiutwp1y5ra9hor4e0h6"
} ]
}
}, {
"name" : "hdfs-NAMENODE-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "NAMENODE",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "autofailover_enabled",
"value" : "true"
}, {
"name" : "dfs_federation_namenode_nameservice",
"value" : "nameservice1"
}, {
"name" : "dfs_namenode_quorum_journal_name",
"value" : "nameservice1"
}, {
"name" : "namenode_id",
"value" : "149"
}, {
"name" : "role_jceks_password",
"value" : "cqkcbrqsq2k6ztgw82q8ksrwx"
} ]
}
}, {
"name" : "hdfs-NAMENODE-bafb4828c9bbc315072f6c52193b5f45",
"type" : "NAMENODE",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "autofailover_enabled",
"value" : "true"
}, {
"name" : "dfs_federation_namenode_nameservice",
"value" : "nameservice1"
}, {
"name" : "dfs_namenode_quorum_journal_name",
"value" : "nameservice1"
}, {
"name" : "namenode_id",
"value" : "132"
}, {
"name" : "role_jceks_password",
"value" : "3txbyg4hycp3l1y3lnsf3yp30"
} ]
}
} ],
"displayName" : "HDFS"
}, {
"name" : "yarn",
"type" : "YARN",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "GATEWAY",
"items" : [ {
"name" : "mapred_reduce_tasks",
"value" : "8"
}, {
"name" : "mapred_submit_replication",
"value" : "2"
} ]
}, {
"roleType" : "JOBHISTORY",
"items" : [ {
"name" : "mr2_jobhistory_java_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "NODEMANAGER",
"items" : [ {
"name" : "rm_cpu_shares",
"value" : "1600"
}, {
"name" : "rm_io_weight",
"value" : "800"
}, {
"name" : "yarn_nodemanager_heartbeat_interval_ms",
"value" : "100"
}, {
"name" : "yarn_nodemanager_local_dirs",
"value" : "/yarn/nm"
}, {
"name" : "yarn_nodemanager_log_dirs",
"value" : "/yarn/container-logs"
}, {
"name" : "yarn_nodemanager_resource_cpu_vcores",
"value" : "3"
}, {
"name" : "yarn_nodemanager_resource_memory_mb",
"value" : "3537"
} ]
}, {
"roleType" : "RESOURCEMANAGER",
"items" : [ {
"name" : "resource_manager_java_heapsize",
"value" : "593494016"
}, {
"name" : "yarn_scheduler_maximum_allocation_mb",
"value" : "4939"
}, {
"name" : "yarn_scheduler_maximum_allocation_vcores",
"value" : "3"
} ]
} ],
"items" : [ {
"name" : "hdfs_service",
"value" : "hdfs"
}, {
"name" : "rm_dirty",
"value" : "false"
}, {
"name" : "rm_last_allocation_percentage",
"value" : "80"
}, {
"name" : "yarn_service_cgroups",
"value" : "false"
}, {
"name" : "yarn_service_lce_always",
"value" : "false"
}, {
"name" : "zk_authorization_secret_key",
"value" : "sWWXo6GMX8rPqH6tpXXqSMDIBPjcqJ"
}, {
"name" : "zookeeper_service",
"value" : "zookeeper"
} ]
},
"roles" : [ {
"name" : "yarn-JOBHISTORY-bafb4828c9bbc315072f6c52193b5f45",
"type" : "JOBHISTORY",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "3bgbpfezxthva17y8s1xk6kp"
} ]
}
}, {
"name" : "yarn-NODEMANAGER-186261d19970f21ff6b566a28b59abf7",
"type" : "NODEMANAGER",
"hostRef" : {
"hostId" : "i-096dde2d24aee520b"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "d6or4mfe41czh3tdn16o8spe9"
} ]
}
}, {
"name" : "yarn-NODEMANAGER-28d425e2b5cce716b08c2b8cb100de68",
"type" : "NODEMANAGER",
"hostRef" : {
"hostId" : "i-0d83575d8d57c4233"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "1psj97x7gglchi8n2aicdc4bs"
} ]
}
}, {
"name" : "yarn-NODEMANAGER-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "NODEMANAGER",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "7uls7fxvu3sysly82opkeku8k"
} ]
}
}, {
"name" : "yarn-NODEMANAGER-bfd01a4bc9574e3d724decaa1b03ab6e",
"type" : "NODEMANAGER",
"hostRef" : {
"hostId" : "i-06f2256b7d2e0fd5a"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "d5dqdmdkda5bdgzgjlo9wbyy5"
} ]
}
}, {
"name" : "yarn-RESOURCEMANAGER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "RESOURCEMANAGER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "rm_id",
"value" : "139"
}, {
"name" : "role_jceks_password",
"value" : "67t7mr61yoie0edtuqwd6xnpp"
} ]
}
} ],
"displayName" : "YARN (MR2 Included)"
}, {
"name" : "hive",
"type" : "HIVE",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "HIVEMETASTORE",
"items" : [ {
"name" : "hive_metastore_java_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "HIVESERVER2",
"items" : [ {
"name" : "hiveserver2_java_heapsize",
"value" : "593494016"
}, {
"name" : "hiveserver2_spark_driver_memory",
"value" : "966367641"
}, {
"name" : "hiveserver2_spark_executor_cores",
"value" : "4"
}, {
"name" : "hiveserver2_spark_executor_memory",
"value" : "4402079334"
}, {
"name" : "hiveserver2_spark_yarn_driver_memory_overhead",
"value" : "102"
}, {
"name" : "hiveserver2_spark_yarn_executor_memory_overhead",
"value" : "740"
} ]
} ],
"items" : [ {
"name" : "hive_metastore_database_host",
"value" : "ip-172-31-90-35.ec2.internal"
}, {
"name" : "hive_metastore_database_password",
"value" : "mariadb"
}, {
"name" : "hive_metastore_database_user",
"value" : "mariadbuser"
}, {
"name" : "mapreduce_yarn_service",
"value" : "yarn"
}, {
"name" : "zookeeper_service",
"value" : "zookeeper"
} ]
},
"roles" : [ {
"name" : "hive-GATEWAY-186261d19970f21ff6b566a28b59abf7",
"type" : "GATEWAY",
"hostRef" : {
"hostId" : "i-096dde2d24aee520b"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hive-GATEWAY-28d425e2b5cce716b08c2b8cb100de68",
"type" : "GATEWAY",
"hostRef" : {
"hostId" : "i-0d83575d8d57c4233"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hive-GATEWAY-5cba4e5e2189dc1936dbb6f44c014da3",
"type" : "GATEWAY",
"hostRef" : {
"hostId" : "i-098b99d366cdbf11f"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hive-GATEWAY-bafb4828c9bbc315072f6c52193b5f45",
"type" : "GATEWAY",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hive-GATEWAY-bfd01a4bc9574e3d724decaa1b03ab6e",
"type" : "GATEWAY",
"hostRef" : {
"hostId" : "i-06f2256b7d2e0fd5a"
},
"config" : {
"items" : [ ]
}
}, {
"name" : "hive-HIVEMETASTORE-bafb4828c9bbc315072f6c52193b5f45",
"type" : "HIVEMETASTORE",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "5qdaffphz1ms04dtz5zbwbs37"
} ]
}
}, {
"name" : "hive-HIVESERVER2-bafb4828c9bbc315072f6c52193b5f45",
"type" : "HIVESERVER2",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "2fuoi8pwjb3ea0j7zt46r8hqb"
} ]
}
} ],
"displayName" : "Hive"
} ]
} ],
"hosts" : [ {
"hostId" : "i-096dde2d24aee520b",
"ipAddress" : "172.31.86.146",
"hostname" : "ip-172-31-86-146.ec2.internal",
"rackId" : "/default",
"config" : {
"items" : [ ]
}
}, {
"hostId" : "i-098b99d366cdbf11f",
"ipAddress" : "172.31.87.246",
"hostname" : "ip-172-31-87-246.ec2.internal",
"rackId" : "/default",
"config" : {
"items" : [ ]
}
}, {
"hostId" : "i-0d83575d8d57c4233",
"ipAddress" : "172.31.89.87",
"hostname" : "ip-172-31-89-87.ec2.internal",
"rackId" : "/default",
"config" : {
"items" : [ ]
}
}, {
"hostId" : "i-06ade185c18a6ee43",
"ipAddress" : "172.31.90.35",
"hostname" : "ip-172-31-90-35.ec2.internal",
"rackId" : "/default",
"config" : {
"items" : [ ]
}
}, {
"hostId" : "i-06f2256b7d2e0fd5a",
"ipAddress" : "172.31.95.78",
"hostname" : "ip-172-31-95-78.ec2.internal",
"rackId" : "/default",
"config" : {
"items" : [ ]
}
} ],
"users" : [ {
"name" : "__cloudera_internal_user__mgmt-EVENTSERVER-bafb4828c9bbc315072f6c52193b5f45",
"roles" : [ "ROLE_USER" ],
"pwHash" : "0105fa166709ff4f6849dd569e2d4f82b8a9684eeee81e99c1243b2bfcd2e284",
"pwSalt" : -9089038186276525546,
"pwLogin" : true
}, {
"name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-bafb4828c9bbc315072f6c52193b5f45",
"roles" : [ "ROLE_USER" ],
"pwHash" : "1386fb7a61819628386027f2ff4e85f174cb540b0ee86de93a547b9f95ab50e0",
"pwSalt" : -3674072910921056019,
"pwLogin" : true
}, {
"name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-bafb4828c9bbc315072f6c52193b5f45",
"roles" : [ "ROLE_USER" ],
"pwHash" : "81d407067c8d7cabf1e6d300c12d5587577f9979ce20c2facc794bcb0332dafc",
"pwSalt" : 4427558710196294419,
"pwLogin" : true
}, {
"name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-bafb4828c9bbc315072f6c52193b5f45",
"roles" : [ "ROLE_USER" ],
"pwHash" : "0446944c60929d06c4f8ee44edd4c8f0332c80b9f113ac4428c5a45efbc56bc4",
"pwSalt" : 8922193198462780856,
"pwLogin" : true
}, {
"name" : "admin",
"roles" : [ "ROLE_ADMIN" ],
"pwHash" : "2abee7e07fd7fe973c0ea35dad3d8ce5098b50bc216a4f74148119ba074f9ae8",
"pwSalt" : 3124328611618346980,
"pwLogin" : true
}, {
"name" : "minotaur",
"roles" : [ "ROLE_OPERATOR" ],
"pwHash" : "fc383e4ab253148d179e008059c2f895e1930ff5e8fdcea4e8c199a59acfcf82",
"pwSalt" : 3918364210350810598,
"pwLogin" : true
}, {
"name" : "rahulsarda1",
"roles" : [ "ROLE_LIMITED" ],
"pwHash" : "d3ffa81f0cda793fb868f085860ec02b520aafebfce89ff2f7a272b6322da315",
"pwSalt" : -6836226185397207882,
"pwLogin" : true
} ],
"versionInfo" : {
"version" : "5.9.3",
"buildUser" : "jenkins",
"buildTimestamp" : "20170627-1506",
"gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
"snapshot" : false
},
"managementService" : {
"name" : "mgmt",
"type" : "MGMT",
"config" : {
"roleTypeConfigs" : [ {
"roleType" : "EVENTSERVER",
"items" : [ {
"name" : "event_server_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "HOSTMONITOR",
"items" : [ {
"name" : "firehose_heapsize",
"value" : "593494016"
}, {
"name" : "firehose_non_java_memory_bytes",
"value" : "805306368"
} ]
}, {
"roleType" : "REPORTSMANAGER",
"items" : [ {
"name" : "headlamp_database_host",
"value" : "ip-172-31-90-35.ec2.internal"
}, {
"name" : "headlamp_database_name",
"value" : "rman"
}, {
"name" : "headlamp_database_password",
"value" : "mariadb"
}, {
"name" : "headlamp_database_user",
"value" : "mariadbuser"
}, {
"name" : "headlamp_heapsize",
"value" : "593494016"
} ]
}, {
"roleType" : "SERVICEMONITOR",
"items" : [ {
"name" : "firehose_heapsize",
"value" : "593494016"
}, {
"name" : "firehose_non_java_memory_bytes",
"value" : "805306368"
} ]
} ],
"items" : [ ]
},
"roles" : [ {
"name" : "mgmt-ALERTPUBLISHER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "ALERTPUBLISHER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "7b9r57bsmmwk9gxevntl95u78"
} ]
}
}, {
"name" : "mgmt-EVENTSERVER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "EVENTSERVER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "basybhhm4m3whi77zwooksbie"
} ]
}
}, {
"name" : "mgmt-HOSTMONITOR-bafb4828c9bbc315072f6c52193b5f45",
"type" : "HOSTMONITOR",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "ejti94v2tid0ag733fj5pkij6"
} ]
}
}, {
"name" : "mgmt-REPORTSMANAGER-bafb4828c9bbc315072f6c52193b5f45",
"type" : "REPORTSMANAGER",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "mzj1v8biz2lmnmbxu927zo9h"
} ]
}
}, {
"name" : "mgmt-SERVICEMONITOR-bafb4828c9bbc315072f6c52193b5f45",
"type" : "SERVICEMONITOR",
"hostRef" : {
"hostId" : "i-06ade185c18a6ee43"
},
"config" : {
"items" : [ {
"name" : "role_jceks_password",
"value" : "bhvixl6gatecnctyenjden5q0"
} ]
}
} ],
"displayName" : "Cloudera Management Service"
},
"managerSettings" : {
"items" : [ {
"name" : "CLUSTER_STATS_START",
"value" : "10/26/2012 19:10"
}, {
"name" : "PUBLIC_CLOUD_STATUS",
"value" : "ON_PUBLIC_CLOUD"
}, {
"name" : "REMOTE_PARCEL_REPO_URLS",
"value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
} ]
}
}
```



