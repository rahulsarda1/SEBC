# Add user principal using cloudera-scm

## login as cloudera-scm
```sh
kadmin.local -p cloudera-scm@CDHBOOTCAMP.COM
```
## create Keytab and user rahulsarda1
```sh
sudo mkdir /etc/security/keytabs

kadmin.local:  addprinc -randkey rahulsarda1@CDHBOOTCAMP.COM
Principal "rahulsarda1@CDHBOOTCAMP.COM" created.

xst -k rahulsarda1.user.keytab rahulsarda1@CDHBOOTCAMP.COM

mv rahulsarda1.user.keytab /etc/security/keytabs/.
```
## Provide rights to the file for the user
```sh
chown rahulsarda1 rahulsarda1-user.keytab
```
## Login  and perform kinit and klist commands
```sh
su rahulsarda1
kinit rahulsarda1@CDHBOOTCAMP.COM -k -t /etc/security/keytabs/rahulsarda1-user.keytab
klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: rahulsarda1@CDHBOOTCAMP.COM

Valid starting       Expires              Service principal
10/11/2017 19:31:49  10/12/2017 19:31:49  krbtgt/CDHBOOTCAMP.COM@CDHBOOTCAMP.COM
renew until 10/18/2017 19:31:49
```



