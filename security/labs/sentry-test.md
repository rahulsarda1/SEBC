
# Sentry Setup Links
https://www.cloudera.com/documentation/enterprise/latest/topics/sg_sentry_service_config.html

Refer the link for autmated Sentry Service Installation
https://www.cloudera.com/documentation/enterprise/5-12-x/topics/sg_sentry_service_install.html

# Verify user privileges
```sh
[root@ip-172-31-90-163 conf]# su rahulsarda1
[rahulsarda1@ip-172-31-90-163 conf]$ kinit
Password for rahulsarda1@CDHBOOTCAMP.COM:
[rahulsarda1@ip-172-31-90-163 conf]$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: rahulsarda1@CDHBOOTCAMP.COM

Valid starting       Expires              Service principal
10/12/2017 12:26:02  10/13/2017 12:26:02  krbtgt/CDHBOOTCAMP.COM@CDHBOOTCAMP.COM
renew until 10/19/2017 12:26:02
[rahulsarda1@ip-172-31-90-163 conf]$ beeline
Beeline version 1.1.0-cdh5.13.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.0)
Driver: Hive JDBC (version 1.1.0-cdh5.13.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20171012122626_96ad02ce-f22c-4d39-b4f9-c6b36433bb1e): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171012122626_96ad02ce-f22c-4d39-b4f9-c6b36433bb1e); Time taken: 0.077 seconds
INFO  : Executing command(queryId=hive_20171012122626_96ad02ce-f22c-4d39-b4f9-c6b36433bb1e): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012122626_96ad02ce-f22c-4d39-b4f9-c6b36433bb1e); Time taken: 0.134 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.306 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>
```

# Create a Sentry role with full authorization
```sh
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171012122828_432d7a8f-44dc-4612-be41-74ec741b078a): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012122828_432d7a8f-44dc-4612-be41-74ec741b078a); Time taken: 0.074 seconds
INFO  : Executing command(queryId=hive_20171012122828_432d7a8f-44dc-4612-be41-74ec741b078a): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012122828_432d7a8f-44dc-4612-be41-74ec741b078a); Time taken: 0.013 seconds
INFO  : OK
No rows affected (0.102 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171012122828_5f21a361-b98d-4f4f-b18d-9e644aa1ac8f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012122828_5f21a361-b98d-4f4f-b18d-9e644aa1ac8f); Time taken: 0.085 seconds
INFO  : Executing command(queryId=hive_20171012122828_5f21a361-b98d-4f4f-b18d-9e644aa1ac8f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012122828_5f21a361-b98d-4f4f-b18d-9e644aa1ac8f); Time taken: 0.072 seconds
INFO  : OK
No rows affected (0.182 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT ROLE sentry_admin TO GROUP {your_primary};
Error: Error while compiling statement: FAILED: ParseException line 1:33 cannot recognize input near '{' 'your_primary' '}' in identifier for principal spec (state=42000,code=40000)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT ROLE sentry_admin TO GROUP sentryadmin;
INFO  : Compiling command(queryId=hive_20171012123030_5c4a019a-daf5-4a0e-95d7-9509cc4e3466): GRANT ROLE sentry_admin TO GROUP sentryadmin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012123030_5c4a019a-daf5-4a0e-95d7-9509cc4e3466); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20171012123030_5c4a019a-daf5-4a0e-95d7-9509cc4e3466): GRANT ROLE sentry_admin TO GROUP sentryadmin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012123030_5c4a019a-daf5-4a0e-95d7-9509cc4e3466); Time taken: 0.066 seconds
INFO  : OK
No rows affected (0.155 seconds)
INFO  : Compiling command(queryId=hive_20171012123838_bcd6846a-5169-4e5e-8947-454f212c4b5e): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171012123838_bcd6846a-5169-4e5e-8947-454f212c4b5e); Time taken: 0.078 seconds
INFO  : Executing command(queryId=hive_20171012123838_bcd6846a-5169-4e5e-8947-454f212c4b5e): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012123838_bcd6846a-5169-4e5e-8947-454f212c4b5e); Time taken: 0.12 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
+------------+--+
1 row selected (0.246 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>
```

# Create additional test users

```sh
hosts file contains
ip-172-31-90-163.ec2.internal
ip-172-31-90-157.ec2.internal
ip-172-31-91-100.ec2.internal
ip-172-31-89-10.ec2.internal
ip-172-31-80-39.ec2.internal

for i in `cat ~/hosts`; do echo $i; ssh $i "groupadd selector"; done

[root@ip-172-31-90-163 ~]# for i in `cat ~/hosts`; do echo $i; ssh $i "groupadd selector"; done
ip-172-31-90-163.ec2.internal
ip-172-31-90-157.ec2.internal
ip-172-31-91-100.ec2.internal
ip-172-31-89-10.ec2.internal
ip-172-31-80-39.ec2.internal
[root@ip-172-31-90-163 ~]#
[root@ip-172-31-90-163 ~]# for i in `cat ~/hosts`; do echo $i; ssh $i "groupadd inserters"; done
ip-172-31-90-163.ec2.internal
ip-172-31-90-157.ec2.internal
ip-172-31-91-100.ec2.internal
ip-172-31-89-10.ec2.internal
ip-172-31-80-39.ec2.internal
[root@ip-172-31-90-163 ~]# for i in `cat ~/hosts`; do echo $i; ssh $i "useradd -u 1100 -g selector george"; done
ip-172-31-90-163.ec2.internal
ip-172-31-90-157.ec2.internal
ip-172-31-91-100.ec2.internal
ip-172-31-89-10.ec2.internal
ip-172-31-80-39.ec2.internal
[root@ip-172-31-90-163 ~]# for i in `cat ~/hosts`; do echo $i; ssh $i "useradd -u 1200 -g inserters ferdinand"; done
ip-172-31-90-163.ec2.internal
ip-172-31-90-157.ec2.internal
ip-172-31-91-100.ec2.internal
ip-172-31-89-10.ec2.internal
ip-172-31-80-39.ec2.internal
[root@ip-172-31-90-163 conf]# kadmin.local
Authenticating as principal hdfs/admin@CDHBOOTCAMP.COM with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@CDHBOOTCAMP.COM; defaulting to no policy
Enter password for principal "george@CDHBOOTCAMP.COM":
Re-enter password for principal "george@CDHBOOTCAMP.COM":
Principal "george@CDHBOOTCAMP.COM" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@CDHBOOTCAMP.COM; defaulting to no policy
Enter password for principal "ferdinand@CDHBOOTCAMP.COM":
Re-enter password for principal "ferdinand@CDHBOOTCAMP.COM":
Principal "ferdinand@CDHBOOTCAMP.COM" created.
kadmin.local:

```
# CREATE TEST ROLES
```sh
[rahulsarda1@ip-172-31-90-163 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: rahulsarda1@CDHBOOTCAMP.COM

Valid starting       Expires              Service principal
10/12/2017 12:26:02  10/13/2017 12:26:02  krbtgt/CDHBOOTCAMP.COM@CDHBOOTCAMP.COM
renew until 10/19/2017 12:26:02
[rahulsarda1@ip-172-31-90-163 ~]$ beeline
Beeline version 1.1.0-cdh5.13.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.0)
Driver: Hive JDBC (version 1.1.0-cdh5.13.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20171012124949_b6cc1a57-4d2c-4a0e-87f2-683055509e03): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012124949_b6cc1a57-4d2c-4a0e-87f2-683055509e03); Time taken: 0.091 seconds
INFO  : Executing command(queryId=hive_20171012124949_b6cc1a57-4d2c-4a0e-87f2-683055509e03): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012124949_b6cc1a57-4d2c-4a0e-87f2-683055509e03); Time taken: 0.021 seconds
INFO  : OK
No rows affected (0.187 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20171012124949_080722c9-4673-4405-97be-227c2738d182): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012124949_080722c9-4673-4405-97be-227c2738d182); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20171012124949_080722c9-4673-4405-97be-227c2738d182): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012124949_080722c9-4673-4405-97be-227c2738d182); Time taken: 0.012 seconds
INFO  : OK
No rows affected (0.086 seconds)
```

# Grant read privilege for all tables to reads

```sh
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20171012125050_3ba761e7-a304-4c7f-af4e-8e77115ced5f): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125050_3ba761e7-a304-4c7f-af4e-8e77115ced5f); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20171012125050_3ba761e7-a304-4c7f-af4e-8e77115ced5f): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125050_3ba761e7-a304-4c7f-af4e-8e77115ced5f); Time taken: 0.016 seconds
INFO  : OK
No rows affected (0.096 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20171012125050_fde59df8-09ff-431c-b5f8-c42a166d47bc): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125050_fde59df8-09ff-431c-b5f8-c42a166d47bc); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20171012125050_fde59df8-09ff-431c-b5f8-c42a166d47bc): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125050_fde59df8-09ff-431c-b5f8-c42a166d47bc); Time taken: 0.014 seconds
INFO  : OK
No rows affected (0.09 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>
```

# Grant read privilege for default.sample07 only to 'writes':

```sh
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20171012125151_29b60ac9-a300-48c8-b529-0539fa958f3c): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125151_29b60ac9-a300-48c8-b529-0539fa958f3c); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20171012125151_29b60ac9-a300-48c8-b529-0539fa958f3c): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125151_29b60ac9-a300-48c8-b529-0539fa958f3c); Time taken: 0.053 seconds
INFO  : OK
No rows affected (0.129 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20171012125151_2654d97e-05cf-47d7-be23-12e82dd49609): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125151_2654d97e-05cf-47d7-be23-12e82dd49609); Time taken: 0.09 seconds
INFO  : Executing command(queryId=hive_20171012125151_2654d97e-05cf-47d7-be23-12e82dd49609): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125151_2654d97e-05cf-47d7-be23-12e82dd49609); Time taken: 0.017 seconds
INFO  : OK
No rows affected (0.12 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20171012125151_5b43d875-1e4c-468d-b4fc-3f3454fe343a): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125151_5b43d875-1e4c-468d-b4fc-3f3454fe343a); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20171012125151_5b43d875-1e4c-468d-b4fc-3f3454fe343a): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125151_5b43d875-1e4c-468d-b4fc-3f3454fe343a); Time taken: 0.013 seconds
INFO  : OK
No rows affected (0.087 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>
```

# kinit as george, then login to beeline

```sh
[rahulsarda1@ip-172-31-90-163 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: george@CDHBOOTCAMP.COM

Valid starting       Expires              Service principal
10/12/2017 12:53:26  10/13/2017 12:53:26  krbtgt/CDHBOOTCAMP.COM@CDHBOOTCAMP.COM
renew until 10/19/2017 12:53:26
[rahulsarda1@ip-172-31-90-163 ~]$ beeline
Beeline version 1.1.0-cdh5.13.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.0)
Driver: Hive JDBC (version 1.1.0-cdh5.13.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171012125454_368b12a8-6913-48bf-8717-5c2dfd1fa6ab): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125454_368b12a8-6913-48bf-8717-5c2dfd1fa6ab); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20171012125454_368b12a8-6913-48bf-8717-5c2dfd1fa6ab): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125454_368b12a8-6913-48bf-8717-5c2dfd1fa6ab); Time taken: 0.122 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
+------------+--+
1 row selected (0.292 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>
[rahulsarda1@ip-172-31-90-163 ~]$ kinit ferdinand
Password for ferdinand@CDHBOOTCAMP.COM:
[rahulsarda1@ip-172-31-90-163 ~]$ beeline
Beeline version 1.1.0-cdh5.13.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-90-163.ec2.internal:10000/default;principal=hive/ip-172-31-90-163.ec2.internal@CDHBOOTCAMP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.0)
Driver: Hive JDBC (version 1.1.0-cdh5.13.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-90-163.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20171012125757_d46d2627-7979-4b2e-bfca-cc04430ce14b): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171012125757_d46d2627-7979-4b2e-bfca-cc04430ce14b); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20171012125757_d46d2627-7979-4b2e-bfca-cc04430ce14b): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171012125757_d46d2627-7979-4b2e-bfca-cc04430ce14b); Time taken: 0.136 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
| sample_07 |
+-----------+--+
No rows selected (0.306 seconds)
0: jdbc:hive2://ip-172-31-90-163.ec2.internal>

```

