
# Backing up Databases
```sh
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb amon > backup/amon-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb rman > backup/rman-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb metastore > backup/metastore-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb sentry > backup/sentry-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb nav > backup/nav-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb navms > backup/navms-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb hue > backup/hue-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb cmdb > backup/cmdb-backup.sql
mysqldump -hip-172-31-90-35.ec2.internal -umariadbuser -pmariadb oozie > backup/oozie-backup.sql
```

# Results

# Get API version
curl -u 'admin:admin' "http://52.91.189.102:7180/api/version"

```sh
v18
```

# Get CM Version
curl -u 'admin:admin' "http://52.91.189.102:7180/api/v14/cm/version"

```sh
{
"version" : "5.13.0",
"buildUser" : "jenkins",
"buildTimestamp" : "20171002-1719",
"gitHash" : "bd657e597e6743c458ee2c9aabe808b7c972981c",
"snapshot" : false
}
```


# Get users
curl -u 'admin:admin' "http://52.91.189.102:7180/api/v14/users"

```sh
{
"items" : [ {
"name" : "admin",
"roles" : [ "ROLE_ADMIN" ]
}, {
"name" : "minotaur",
"roles" : [ "ROLE_OPERATOR" ]
}, {
"name" : "rahulsarda1",
"roles" : [ "ROLE_LIMITED" ]
} ]
}
```

# Get database server info
curl -u 'admin:admin' "http://52.91.189.102:7180/api/v14/cm/scmDbInfo"

```sh
{
"scmDbType" : "MYSQL",
"embeddedDbUsed" : false
}
```

