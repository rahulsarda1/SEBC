# hive commands

## Stop hive

```sh
curl -u 'admin:admin' -X POST "http://52.91.189.102:7180/api/v12/clusters/rahulsarda1/services/hive/commands/stop"
{
"id" : 648,
"name" : "Stop",
"startTime" : "2017-10-11T16:14:14.724Z",
"active" : true,
"serviceRef" : {
"clusterName" : "cluster",
"serviceName" : "hive"
}
```
## Start Hive
```sh
curl -u 'admin:admin' -X POST "http://52.91.189.102:7180/api/v12/clusters/rahulsarda1/services/hive/commands/start"
{
"id" : 652,
"name" : "Start",
"startTime" : "2017-10-11T16:15:09.606Z",
"active" : true,
"serviceRef" : {
"clusterName" : "cluster",
"serviceName" : "hive"
}
```
## Check Hive

```sh
curl -u 'admin:admin' -X GET "http://52.91.189.102:7180/api/v12/clusters/rahulsarda1/services/hive"
{
"name" : "hive",
"type" : "HIVE",
"clusterRef" : {
"clusterName" : "cluster"
},
"serviceUrl" : "http://ip-172-31-90-35.ec2.internal:7180/cmf/serviceRedirect/hive",
"roleInstancesUrl" : "http://ip-172-31-90-35.ec2.internal:7180/cmf/serviceRedirect/hive/instances",
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
```


