
# What is ubertask optimization?
Ubertask enables grouping several small tasks of a job on a single JVM. Runs "sufficiently small" jobs sequentially within a single JVM.

"Small" is defined by the
mapreduce.job.ubertask.maxmaps,
```sh
Threshold for number of reduces, beyond which a job is considered too big for the ubertask optimization.
```
mapreduce.job.ubertask.maxreduces,
```sh
Threshold for number of maps, beyond which a job is considered too big for the ubertask optimization.
```
mapreduce.job.ubertask.maxbytes settings.
```sh
Threshold for number of input bytes, beyond which a job is considered too big for the ubertask optimization. If no value is specified, dfs.block.size is used as a default
```
# Where in CM is the Kerberos Security Realm value displayed?

Administration > Settings > Kerberos

| Kerberos Security Realm | HADOOP.COM |
| default_realm | |


# Which CDH service(s) host a property for enabling Kerberos authentication?

Every service including the cloudera management has at least a principal setup

# How do you upgrade the CM agents?
Refered to 5.9.x documentation
We have to manually upgrade the package using a new repository for the agent located on the server host and then either manually or through cloudera manager for the rest of the agents

Choose a procedure based on how you installed Cloudera Manager:
- Upgrade and Start Cloudera Manager Agent (Packages)
- Restart Cloudera Manager Agents (Tarballs)

The Cloudera Manager upgrade wizard can upgrade the agent software (and, optionally, the JDK), or we can install the agent and JDK software manually from tarballs. The CDH software is not upgraded during this process.

# Give the tsquery statement used to chart Hue's CPU utilization?

```sh
select total_cpu_user + total_cpu_system where roleType=HUE_SERVER
```
The tsquery language is used to specify statements for retrieving time-series data from the Cloudera Manager time-series datastore.

# Name all the roles that make up the Hive service

Hive metastore, WebHCatalog server, HCatalog, Hiveserver2, Gateway

# What steps must be completed before integrating Cloudera Manager with Kerberos?

Installing KDC server and its clients manually, create its conf files (kdc.conf, krb5.conf on all hosts), set ticket max life and renewable, initiate the database and set admin users that can add principals and generate keytabs

Before using the wizard, ensure that we have performed the following steps:
* Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
* The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
* OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
* Cloudera Manager needs an account that has permissions to create other accounts in the KDC.


