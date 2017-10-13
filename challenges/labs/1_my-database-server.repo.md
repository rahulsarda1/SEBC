# Install MySQL 5.5 or MariaDB 5.5 on the first node listed in 0_setup.md
```sh
First node details - Redhat 7.2 - ip-172-31-84-209.ec2.internal
```
# Use a YUM repository to install the package
```sh
[root@ip-172-31-84-209 ec2-user]# yum install mariadb-server
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Resolving Dependencies
--> Running transaction check
---> Package mariadb-server.x86_64 1:5.5.56-2.el7 will be installed
--> Processing Dependency: mariadb(x86-64) = 1:5.5.56-2.el7 for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: mariadb-libs(x86-64) = 1:5.5.56-2.el7 for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: /usr/bin/perl for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.1)(64bit) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.4)(64bit) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(DBI) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(Data::Dumper) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(File::Basename) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(File::Copy) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(File::Path) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(File::Temp) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(Getopt::Long) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(POSIX) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(Sys::Hostname) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(strict) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl(vars) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl-DBD-MySQL for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: perl-DBI for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Processing Dependency: libaio.so.1()(64bit) for package: 1:mariadb-server-5.5.56-2.el7.x86_64
--> Running transaction check
---> Package libaio.x86_64 0:0.3.109-13.el7 will be installed
---> Package mariadb.x86_64 1:5.5.56-2.el7 will be installed
--> Processing Dependency: perl(Exporter) for package: 1:mariadb-5.5.56-2.el7.x86_64
---> Package mariadb-libs.x86_64 1:5.5.44-2.el7 will be updated
---> Package mariadb-libs.x86_64 1:5.5.56-2.el7 will be an update
---> Package perl.x86_64 4:5.16.3-292.el7 will be installed
--> Processing Dependency: perl-libs = 4:5.16.3-292.el7 for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Scalar::Util) >= 1.10 for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Socket) >= 1.3 for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Carp) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Cwd) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(File::Spec) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(File::Spec::Functions) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(File::Spec::Unix) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Filter::Util::Call) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Pod::Simple::Search) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Pod::Simple::XHTML) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Scalar::Util) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Socket) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Storable) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Time::HiRes) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(Time::Local) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(constant) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(threads) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl(threads::shared) for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl-libs for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: perl-macros for package: 4:perl-5.16.3-292.el7.x86_64
--> Processing Dependency: libperl.so()(64bit) for package: 4:perl-5.16.3-292.el7.x86_64
---> Package perl-DBD-MySQL.x86_64 0:4.023-5.el7 will be installed
---> Package perl-DBI.x86_64 0:1.627-4.el7 will be installed
--> Processing Dependency: perl(RPC::PlClient) >= 0.2000 for package: perl-DBI-1.627-4.el7.x86_64
--> Processing Dependency: perl(RPC::PlServer) >= 0.2001 for package: perl-DBI-1.627-4.el7.x86_64
---> Package perl-Data-Dumper.x86_64 0:2.145-3.el7 will be installed
---> Package perl-File-Path.noarch 0:2.09-2.el7 will be installed
---> Package perl-File-Temp.noarch 0:0.23.01-3.el7 will be installed
---> Package perl-Getopt-Long.noarch 0:2.40-2.el7 will be installed
--> Processing Dependency: perl(Pod::Usage) >= 1.14 for package: perl-Getopt-Long-2.40-2.el7.noarch
--> Processing Dependency: perl(Text::ParseWords) for package: perl-Getopt-Long-2.40-2.el7.noarch
--> Running transaction check
---> Package perl-Carp.noarch 0:1.26-244.el7 will be installed
---> Package perl-Exporter.noarch 0:5.68-3.el7 will be installed
---> Package perl-Filter.x86_64 0:1.49-3.el7 will be installed
---> Package perl-PathTools.x86_64 0:3.40-5.el7 will be installed
---> Package perl-PlRPC.noarch 0:0.2020-14.el7 will be installed
--> Processing Dependency: perl(Net::Daemon) >= 0.13 for package: perl-PlRPC-0.2020-14.el7.noarch
--> Processing Dependency: perl(Compress::Zlib) for package: perl-PlRPC-0.2020-14.el7.noarch
--> Processing Dependency: perl(Net::Daemon::Log) for package: perl-PlRPC-0.2020-14.el7.noarch
--> Processing Dependency: perl(Net::Daemon::Test) for package: perl-PlRPC-0.2020-14.el7.noarch
---> Package perl-Pod-Simple.noarch 1:3.28-4.el7 will be installed
--> Processing Dependency: perl(Pod::Escapes) >= 1.04 for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
--> Processing Dependency: perl(Encode) for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
---> Package perl-Pod-Usage.noarch 0:1.63-3.el7 will be installed
--> Processing Dependency: perl(Pod::Text) >= 3.15 for package: perl-Pod-Usage-1.63-3.el7.noarch
--> Processing Dependency: perl-Pod-Perldoc for package: perl-Pod-Usage-1.63-3.el7.noarch
---> Package perl-Scalar-List-Utils.x86_64 0:1.27-248.el7 will be installed
---> Package perl-Socket.x86_64 0:2.010-4.el7 will be installed
---> Package perl-Storable.x86_64 0:2.45-3.el7 will be installed
---> Package perl-Text-ParseWords.noarch 0:3.29-4.el7 will be installed
---> Package perl-Time-HiRes.x86_64 4:1.9725-3.el7 will be installed
---> Package perl-Time-Local.noarch 0:1.2300-2.el7 will be installed
---> Package perl-constant.noarch 0:1.27-2.el7 will be installed
---> Package perl-libs.x86_64 4:5.16.3-292.el7 will be installed
---> Package perl-macros.x86_64 4:5.16.3-292.el7 will be installed
---> Package perl-threads.x86_64 0:1.87-4.el7 will be installed
---> Package perl-threads-shared.x86_64 0:1.43-6.el7 will be installed
--> Running transaction check
---> Package perl-Encode.x86_64 0:2.51-7.el7 will be installed
---> Package perl-IO-Compress.noarch 0:2.061-2.el7 will be installed
--> Processing Dependency: perl(Compress::Raw::Bzip2) >= 2.061 for package: perl-IO-Compress-2.061-2.el7.noarch
--> Processing Dependency: perl(Compress::Raw::Zlib) >= 2.061 for package: perl-IO-Compress-2.061-2.el7.noarch
---> Package perl-Net-Daemon.noarch 0:0.48-5.el7 will be installed
---> Package perl-Pod-Escapes.noarch 1:1.04-292.el7 will be installed
---> Package perl-Pod-Perldoc.noarch 0:3.20-4.el7 will be installed
--> Processing Dependency: perl(HTTP::Tiny) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
--> Processing Dependency: perl(parent) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
---> Package perl-podlators.noarch 0:2.5.1-3.el7 will be installed
--> Running transaction check
---> Package perl-Compress-Raw-Bzip2.x86_64 0:2.061-3.el7 will be installed
---> Package perl-Compress-Raw-Zlib.x86_64 1:2.061-4.el7 will be installed
---> Package perl-HTTP-Tiny.noarch 0:0.033-3.el7 will be installed
---> Package perl-parent.noarch 1:0.225-244.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

============================================================================================================================================================================================================
Package                                              Arch                                Version                                       Repository                                                     Size
============================================================================================================================================================================================================
Installing:
mariadb-server                                       x86_64                              1:5.5.56-2.el7                                rhui-REGION-rhel-server-releases                               11 M
Installing for dependencies:
libaio                                               x86_64                              0.3.109-13.el7                                rhui-REGION-rhel-server-releases                               24 k
mariadb                                              x86_64                              1:5.5.56-2.el7                                rhui-REGION-rhel-server-releases                              9.1 M
perl                                                 x86_64                              4:5.16.3-292.el7                              rhui-REGION-rhel-server-releases                              8.0 M
perl-Carp                                            noarch                              1.26-244.el7                                  rhui-REGION-rhel-server-releases                               19 k
perl-Compress-Raw-Bzip2                              x86_64                              2.061-3.el7                                   rhui-REGION-rhel-server-releases                               32 k
perl-Compress-Raw-Zlib                               x86_64                              1:2.061-4.el7                                 rhui-REGION-rhel-server-releases                               57 k
perl-DBD-MySQL                                       x86_64                              4.023-5.el7                                   rhui-REGION-rhel-server-releases                              140 k
perl-DBI                                             x86_64                              1.627-4.el7                                   rhui-REGION-rhel-server-releases                              802 k
perl-Data-Dumper                                     x86_64                              2.145-3.el7                                   rhui-REGION-rhel-server-releases                               47 k
perl-Encode                                          x86_64                              2.51-7.el7                                    rhui-REGION-rhel-server-releases                              1.5 M
perl-Exporter                                        noarch                              5.68-3.el7                                    rhui-REGION-rhel-server-releases                               28 k
perl-File-Path                                       noarch                              2.09-2.el7                                    rhui-REGION-rhel-server-releases                               27 k
perl-File-Temp                                       noarch                              0.23.01-3.el7                                 rhui-REGION-rhel-server-releases                               56 k
perl-Filter                                          x86_64                              1.49-3.el7                                    rhui-REGION-rhel-server-releases                               76 k
perl-Getopt-Long                                     noarch                              2.40-2.el7                                    rhui-REGION-rhel-server-releases                               56 k
perl-HTTP-Tiny                                       noarch                              0.033-3.el7                                   rhui-REGION-rhel-server-releases                               38 k
perl-IO-Compress                                     noarch                              2.061-2.el7                                   rhui-REGION-rhel-server-releases                              260 k
perl-Net-Daemon                                      noarch                              0.48-5.el7                                    rhui-REGION-rhel-server-releases                               51 k
perl-PathTools                                       x86_64                              3.40-5.el7                                    rhui-REGION-rhel-server-releases                               83 k
perl-PlRPC                                           noarch                              0.2020-14.el7                                 rhui-REGION-rhel-server-releases                               36 k
perl-Pod-Escapes                                     noarch                              1:1.04-292.el7                                rhui-REGION-rhel-server-releases                               51 k
perl-Pod-Perldoc                                     noarch                              3.20-4.el7                                    rhui-REGION-rhel-server-releases                               87 k
perl-Pod-Simple                                      noarch                              1:3.28-4.el7                                  rhui-REGION-rhel-server-releases                              216 k
perl-Pod-Usage                                       noarch                              1.63-3.el7                                    rhui-REGION-rhel-server-releases                               27 k
perl-Scalar-List-Utils                               x86_64                              1.27-248.el7                                  rhui-REGION-rhel-server-releases                               36 k
perl-Socket                                          x86_64                              2.010-4.el7                                   rhui-REGION-rhel-server-releases                               49 k
perl-Storable                                        x86_64                              2.45-3.el7                                    rhui-REGION-rhel-server-releases                               77 k
perl-Text-ParseWords                                 noarch                              3.29-4.el7                                    rhui-REGION-rhel-server-releases                               14 k
perl-Time-HiRes                                      x86_64                              4:1.9725-3.el7                                rhui-REGION-rhel-server-releases                               45 k
perl-Time-Local                                      noarch                              1.2300-2.el7                                  rhui-REGION-rhel-server-releases                               24 k
perl-constant                                        noarch                              1.27-2.el7                                    rhui-REGION-rhel-server-releases                               19 k
perl-libs                                            x86_64                              4:5.16.3-292.el7                              rhui-REGION-rhel-server-releases                              688 k
perl-macros                                          x86_64                              4:5.16.3-292.el7                              rhui-REGION-rhel-server-releases                               43 k
perl-parent                                          noarch                              1:0.225-244.el7                               rhui-REGION-rhel-server-releases                               12 k
perl-podlators                                       noarch                              2.5.1-3.el7                                   rhui-REGION-rhel-server-releases                              112 k
perl-threads                                         x86_64                              1.87-4.el7                                    rhui-REGION-rhel-server-releases                               49 k
perl-threads-shared                                  x86_64                              1.43-6.el7                                    rhui-REGION-rhel-server-releases                               39 k
Updating for dependencies:
mariadb-libs                                         x86_64                              1:5.5.56-2.el7                                rhui-REGION-rhel-server-releases                              757 k

Transaction Summary
============================================================================================================================================================================================================
Install  1 Package  (+37 Dependent packages)
Upgrade             (  1 Dependent package)

Total download size: 34 M
Is this ok [y/d/N]: y
Downloading packages:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
(1/39): libaio-0.3.109-13.el7.x86_64.rpm                                                                                                                                             |  24 kB  00:00:00
(2/39): mariadb-5.5.56-2.el7.x86_64.rpm                                                                                                                                              | 9.1 MB  00:00:00
(3/39): mariadb-server-5.5.56-2.el7.x86_64.rpm                                                                                                                                       |  11 MB  00:00:00
(4/39): mariadb-libs-5.5.56-2.el7.x86_64.rpm                                                                                                                                         | 757 kB  00:00:00
(5/39): perl-5.16.3-292.el7.x86_64.rpm                                                                                                                                               | 8.0 MB  00:00:00
(6/39): perl-Compress-Raw-Bzip2-2.061-3.el7.x86_64.rpm                                                                                                                               |  32 kB  00:00:00
(7/39): perl-Carp-1.26-244.el7.noarch.rpm                                                                                                                                            |  19 kB  00:00:00
(8/39): perl-DBD-MySQL-4.023-5.el7.x86_64.rpm                                                                                                                                        | 140 kB  00:00:00
(9/39): perl-Data-Dumper-2.145-3.el7.x86_64.rpm                                                                                                                                      |  47 kB  00:00:00
(10/39): perl-DBI-1.627-4.el7.x86_64.rpm                                                                                                                                             | 802 kB  00:00:00
(11/39): perl-Compress-Raw-Zlib-2.061-4.el7.x86_64.rpm                                                                                                                               |  57 kB  00:00:00
(12/39): perl-Encode-2.51-7.el7.x86_64.rpm                                                                                                                                           | 1.5 MB  00:00:00
(13/39): perl-File-Path-2.09-2.el7.noarch.rpm                                                                                                                                        |  27 kB  00:00:00
(14/39): perl-Exporter-5.68-3.el7.noarch.rpm                                                                                                                                         |  28 kB  00:00:00
(15/39): perl-Filter-1.49-3.el7.x86_64.rpm                                                                                                                                           |  76 kB  00:00:00
(16/39): perl-HTTP-Tiny-0.033-3.el7.noarch.rpm                                                                                                                                       |  38 kB  00:00:00
(17/39): perl-File-Temp-0.23.01-3.el7.noarch.rpm                                                                                                                                     |  56 kB  00:00:00
(18/39): perl-Getopt-Long-2.40-2.el7.noarch.rpm                                                                                                                                      |  56 kB  00:00:00
(19/39): perl-Net-Daemon-0.48-5.el7.noarch.rpm                                                                                                                                       |  51 kB  00:00:00
(20/39): perl-PlRPC-0.2020-14.el7.noarch.rpm                                                                                                                                         |  36 kB  00:00:00
(21/39): perl-IO-Compress-2.061-2.el7.noarch.rpm                                                                                                                                     | 260 kB  00:00:00
(22/39): perl-Pod-Escapes-1.04-292.el7.noarch.rpm                                                                                                                                    |  51 kB  00:00:00
(23/39): perl-Pod-Perldoc-3.20-4.el7.noarch.rpm                                                                                                                                      |  87 kB  00:00:00
(24/39): perl-PathTools-3.40-5.el7.x86_64.rpm                                                                                                                                        |  83 kB  00:00:00
(25/39): perl-Pod-Simple-3.28-4.el7.noarch.rpm                                                                                                                                       | 216 kB  00:00:00
(26/39): perl-Pod-Usage-1.63-3.el7.noarch.rpm                                                                                                                                        |  27 kB  00:00:00
(27/39): perl-Scalar-List-Utils-1.27-248.el7.x86_64.rpm                                                                                                                              |  36 kB  00:00:00
(28/39): perl-Socket-2.010-4.el7.x86_64.rpm                                                                                                                                          |  49 kB  00:00:00
(29/39): perl-Text-ParseWords-3.29-4.el7.noarch.rpm                                                                                                                                  |  14 kB  00:00:00
(30/39): perl-Time-HiRes-1.9725-3.el7.x86_64.rpm                                                                                                                                     |  45 kB  00:00:00
(31/39): perl-Storable-2.45-3.el7.x86_64.rpm                                                                                                                                         |  77 kB  00:00:00
(32/39): perl-constant-1.27-2.el7.noarch.rpm                                                                                                                                         |  19 kB  00:00:00
(33/39): perl-Time-Local-1.2300-2.el7.noarch.rpm                                                                                                                                     |  24 kB  00:00:00
(34/39): perl-libs-5.16.3-292.el7.x86_64.rpm                                                                                                                                         | 688 kB  00:00:00
(35/39): perl-macros-5.16.3-292.el7.x86_64.rpm                                                                                                                                       |  43 kB  00:00:00
(36/39): perl-parent-0.225-244.el7.noarch.rpm                                                                                                                                        |  12 kB  00:00:00
(37/39): perl-threads-1.87-4.el7.x86_64.rpm                                                                                                                                          |  49 kB  00:00:00
(38/39): perl-threads-shared-1.43-6.el7.x86_64.rpm                                                                                                                                   |  39 kB  00:00:00
(39/39): perl-podlators-2.5.1-3.el7.noarch.rpm                                                                                                                                       | 112 kB  00:00:00
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                        22 MB/s |  34 MB  00:00:01
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Updating   : 1:mariadb-libs-5.5.56-2.el7.x86_64                                                                                                                                                      1/40
Installing : 1:perl-parent-0.225-244.el7.noarch                                                                                                                                                      2/40
Installing : perl-HTTP-Tiny-0.033-3.el7.noarch                                                                                                                                                       3/40
Installing : perl-podlators-2.5.1-3.el7.noarch                                                                                                                                                       4/40
Installing : perl-Pod-Perldoc-3.20-4.el7.noarch                                                                                                                                                      5/40
Installing : 1:perl-Pod-Escapes-1.04-292.el7.noarch                                                                                                                                                  6/40
Installing : perl-Text-ParseWords-3.29-4.el7.noarch                                                                                                                                                  7/40
Installing : perl-Encode-2.51-7.el7.x86_64                                                                                                                                                           8/40
Installing : perl-Pod-Usage-1.63-3.el7.noarch                                                                                                                                                        9/40
Installing : 4:perl-macros-5.16.3-292.el7.x86_64                                                                                                                                                    10/40
Installing : 4:perl-libs-5.16.3-292.el7.x86_64                                                                                                                                                      11/40
Installing : perl-Storable-2.45-3.el7.x86_64                                                                                                                                                        12/40
Installing : perl-Exporter-5.68-3.el7.noarch                                                                                                                                                        13/40
Installing : perl-constant-1.27-2.el7.noarch                                                                                                                                                        14/40
Installing : perl-Time-Local-1.2300-2.el7.noarch                                                                                                                                                    15/40
Installing : perl-Socket-2.010-4.el7.x86_64                                                                                                                                                         16/40
Installing : perl-Carp-1.26-244.el7.noarch                                                                                                                                                          17/40
Installing : 4:perl-Time-HiRes-1.9725-3.el7.x86_64                                                                                                                                                  18/40
Installing : perl-PathTools-3.40-5.el7.x86_64                                                                                                                                                       19/40
Installing : perl-Scalar-List-Utils-1.27-248.el7.x86_64                                                                                                                                             20/40
Installing : perl-File-Temp-0.23.01-3.el7.noarch                                                                                                                                                    21/40
Installing : perl-File-Path-2.09-2.el7.noarch                                                                                                                                                       22/40
Installing : perl-threads-shared-1.43-6.el7.x86_64                                                                                                                                                  23/40
Installing : perl-threads-1.87-4.el7.x86_64                                                                                                                                                         24/40
Installing : perl-Filter-1.49-3.el7.x86_64                                                                                                                                                          25/40
Installing : 1:perl-Pod-Simple-3.28-4.el7.noarch                                                                                                                                                    26/40
Installing : perl-Getopt-Long-2.40-2.el7.noarch                                                                                                                                                     27/40
Installing : 4:perl-5.16.3-292.el7.x86_64                                                                                                                                                           28/40
Installing : perl-Data-Dumper-2.145-3.el7.x86_64                                                                                                                                                    29/40
Installing : perl-Compress-Raw-Bzip2-2.061-3.el7.x86_64                                                                                                                                             30/40
Installing : perl-Net-Daemon-0.48-5.el7.noarch                                                                                                                                                      31/40
Installing : 1:perl-Compress-Raw-Zlib-2.061-4.el7.x86_64                                                                                                                                            32/40
Installing : perl-IO-Compress-2.061-2.el7.noarch                                                                                                                                                    33/40
Installing : perl-PlRPC-0.2020-14.el7.noarch                                                                                                                                                        34/40
Installing : perl-DBI-1.627-4.el7.x86_64                                                                                                                                                            35/40
Installing : perl-DBD-MySQL-4.023-5.el7.x86_64                                                                                                                                                      36/40
Installing : 1:mariadb-5.5.56-2.el7.x86_64                                                                                                                                                          37/40
Installing : libaio-0.3.109-13.el7.x86_64                                                                                                                                                           38/40
Installing : 1:mariadb-server-5.5.56-2.el7.x86_64                                                                                                                                                   39/40
Cleanup    : 1:mariadb-libs-5.5.44-2.el7.x86_64                                                                                                                                                     40/40
Verifying  : perl-HTTP-Tiny-0.033-3.el7.noarch                                                                                                                                                       1/40
Verifying  : perl-threads-shared-1.43-6.el7.x86_64                                                                                                                                                   2/40
Verifying  : perl-Storable-2.45-3.el7.x86_64                                                                                                                                                         3/40
Verifying  : perl-IO-Compress-2.061-2.el7.noarch                                                                                                                                                     4/40
Verifying  : perl-Exporter-5.68-3.el7.noarch                                                                                                                                                         5/40
Verifying  : perl-constant-1.27-2.el7.noarch                                                                                                                                                         6/40
Verifying  : perl-PathTools-3.40-5.el7.x86_64                                                                                                                                                        7/40
Verifying  : 4:perl-macros-5.16.3-292.el7.x86_64                                                                                                                                                     8/40
Verifying  : 1:mariadb-server-5.5.56-2.el7.x86_64                                                                                                                                                    9/40
Verifying  : perl-Compress-Raw-Bzip2-2.061-3.el7.x86_64                                                                                                                                             10/40
Verifying  : 1:perl-parent-0.225-244.el7.noarch                                                                                                                                                     11/40
Verifying  : perl-Net-Daemon-0.48-5.el7.noarch                                                                                                                                                      12/40
Verifying  : 4:perl-5.16.3-292.el7.x86_64                                                                                                                                                           13/40
Verifying  : perl-File-Temp-0.23.01-3.el7.noarch                                                                                                                                                    14/40
Verifying  : 1:perl-Pod-Simple-3.28-4.el7.noarch                                                                                                                                                    15/40
Verifying  : perl-Time-Local-1.2300-2.el7.noarch                                                                                                                                                    16/40
Verifying  : 4:perl-libs-5.16.3-292.el7.x86_64                                                                                                                                                      17/40
Verifying  : perl-Pod-Perldoc-3.20-4.el7.noarch                                                                                                                                                     18/40
Verifying  : perl-DBD-MySQL-4.023-5.el7.x86_64                                                                                                                                                      19/40
Verifying  : libaio-0.3.109-13.el7.x86_64                                                                                                                                                           20/40
Verifying  : perl-Socket-2.010-4.el7.x86_64                                                                                                                                                         21/40
Verifying  : perl-Carp-1.26-244.el7.noarch                                                                                                                                                          22/40
Verifying  : perl-Data-Dumper-2.145-3.el7.x86_64                                                                                                                                                    23/40
Verifying  : 4:perl-Time-HiRes-1.9725-3.el7.x86_64                                                                                                                                                  24/40
Verifying  : perl-Scalar-List-Utils-1.27-248.el7.x86_64                                                                                                                                             25/40
Verifying  : 1:perl-Compress-Raw-Zlib-2.061-4.el7.x86_64                                                                                                                                            26/40
Verifying  : 1:perl-Pod-Escapes-1.04-292.el7.noarch                                                                                                                                                 27/40
Verifying  : perl-PlRPC-0.2020-14.el7.noarch                                                                                                                                                        28/40
Verifying  : perl-Pod-Usage-1.63-3.el7.noarch                                                                                                                                                       29/40
Verifying  : perl-DBI-1.627-4.el7.x86_64                                                                                                                                                            30/40
Verifying  : perl-Encode-2.51-7.el7.x86_64                                                                                                                                                          31/40
Verifying  : perl-podlators-2.5.1-3.el7.noarch                                                                                                                                                      32/40
Verifying  : perl-Getopt-Long-2.40-2.el7.noarch                                                                                                                                                     33/40
Verifying  : perl-File-Path-2.09-2.el7.noarch                                                                                                                                                       34/40
Verifying  : perl-threads-1.87-4.el7.x86_64                                                                                                                                                         35/40
Verifying  : perl-Filter-1.49-3.el7.x86_64                                                                                                                                                          36/40
Verifying  : perl-Text-ParseWords-3.29-4.el7.noarch                                                                                                                                                 37/40
Verifying  : 1:mariadb-libs-5.5.56-2.el7.x86_64                                                                                                                                                     38/40
Verifying  : 1:mariadb-5.5.56-2.el7.x86_64                                                                                                                                                          39/40
Verifying  : 1:mariadb-libs-5.5.44-2.el7.x86_64                                                                                                                                                     40/40

Installed:
mariadb-server.x86_64 1:5.5.56-2.el7

Dependency Installed:
libaio.x86_64 0:0.3.109-13.el7                        mariadb.x86_64 1:5.5.56-2.el7                        perl.x86_64 4:5.16.3-292.el7                  perl-Carp.noarch 0:1.26-244.el7
perl-Compress-Raw-Bzip2.x86_64 0:2.061-3.el7          perl-Compress-Raw-Zlib.x86_64 1:2.061-4.el7          perl-DBD-MySQL.x86_64 0:4.023-5.el7           perl-DBI.x86_64 0:1.627-4.el7
perl-Data-Dumper.x86_64 0:2.145-3.el7                 perl-Encode.x86_64 0:2.51-7.el7                      perl-Exporter.noarch 0:5.68-3.el7             perl-File-Path.noarch 0:2.09-2.el7
perl-File-Temp.noarch 0:0.23.01-3.el7                 perl-Filter.x86_64 0:1.49-3.el7                      perl-Getopt-Long.noarch 0:2.40-2.el7          perl-HTTP-Tiny.noarch 0:0.033-3.el7
perl-IO-Compress.noarch 0:2.061-2.el7                 perl-Net-Daemon.noarch 0:0.48-5.el7                  perl-PathTools.x86_64 0:3.40-5.el7            perl-PlRPC.noarch 0:0.2020-14.el7
perl-Pod-Escapes.noarch 1:1.04-292.el7                perl-Pod-Perldoc.noarch 0:3.20-4.el7                 perl-Pod-Simple.noarch 1:3.28-4.el7           perl-Pod-Usage.noarch 0:1.63-3.el7
perl-Scalar-List-Utils.x86_64 0:1.27-248.el7          perl-Socket.x86_64 0:2.010-4.el7                     perl-Storable.x86_64 0:2.45-3.el7             perl-Text-ParseWords.noarch 0:3.29-4.el7
perl-Time-HiRes.x86_64 4:1.9725-3.el7                 perl-Time-Local.noarch 0:1.2300-2.el7                perl-constant.noarch 0:1.27-2.el7             perl-libs.x86_64 4:5.16.3-292.el7
perl-macros.x86_64 4:5.16.3-292.el7                   perl-parent.noarch 1:0.225-244.el7                   perl-podlators.noarch 0:2.5.1-3.el7           perl-threads.x86_64 0:1.87-4.el7
perl-threads-shared.x86_64 0:1.43-6.el7

Dependency Updated:
mariadb-libs.x86_64 1:5.5.56-2.el7

Complete!
[root@ip-172-31-84-209 ec2-user]#
```
# Copy the repo configuration you use to challenges/labs/1_my-database-server.repo.md

```sh
[mariadb]
name = MariaDB-5.5.56
baseurl=https://downloads.mariadb.com/files/MariaDB/mariadb-5.5.56/yum/rhel7-amd64/
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```

# Install the database client package and JDBC connector jar on all node

## Database Client

## JDBC Connector
### Run below script on all the nodes

```sh
wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.44.tar.gz
tar zxvf mysql-connector-java-5.1.44.tar.gz
sudo mkdir -p /usr/share/java/
sudo cp mysql-connector-java-5.1.44/mysql-connector-java-5.1.44-bin.jar /usr/share/java/mysql-connector-java.jar
```

# Start the server and create these databases

## Installed the database as per the earlier lab

### below shows status its running
```sh
[root@ip-172-31-84-209 ~]# sudo systemctl status mariadb.service
● mariadb.service - MariaDB database server
Loaded: loaded (/usr/lib/systemd/system/mariadb.service; enabled; vendor preset: disabled)
Active: active (running) since Fri 2017-10-13 10:54:40 EDT; 5s ago
Process: 12398 ExecStartPost=/usr/libexec/mariadb-wait-ready $MAINPID (code=exited, status=0/SUCCESS)
Process: 12319 ExecStartPre=/usr/libexec/mariadb-prepare-db-dir %n (code=exited, status=0/SUCCESS)
Main PID: 12396 (mysqld_safe)
CGroup: /system.slice/mariadb.service
├─12396 /bin/sh /usr/bin/mysqld_safe --basedir=/usr
└─12807 /usr/libexec/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --log-error=/var/log/mariadb/mariadb.log --pid-file=/var/run/mariadb/mariadb.pid

Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: MySQL manual for more instructions.
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: Please report any problems at http://mariadb.org/jira
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: The latest information about MariaDB is available at http://mariadb.org/.
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: You can find additional information about the MySQL part at:
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: http://dev.mysql.com
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: Consider joining MariaDB's strong and vibrant community:
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mariadb-prepare-db-dir[12319]: https://mariadb.org/get-involved/
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mysqld_safe[12396]: 171013 10:54:30 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
Oct 13 10:54:30 ip-172-31-84-209.ec2.internal mysqld_safe[12396]: 171013 10:54:30 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
Oct 13 10:54:40 ip-172-31-84-209.ec2.internal systemd[1]: Started MariaDB database server.
[root@ip-172-31-84-209 ~]# sudo /usr/bin/mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] Y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
... skipping.

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
- Dropping test database...
... Success!
- Removing privileges on test database...
... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
[root@ip-172-31-84-209 ~]#
```

