---
title: How to install db2 version 10.5 on Linux 
author: thecordrecode
date: 2023-03-20 10:00:00 +0900
categories: [DATABASE,DB2]
tags: [DATABASE,DB2,INSTALL]
---

# How to install DB2 database on Linux

The following installation of the steps required to install db2 server as a root user installation

- Log on to the linux host as root
- Add hostname and ipaddress in /etc/hosts
- Validate network connectivity
- Create Users and Groups for DB2, Modify the group and user IDs if required for your system.

# STEP1 Create Users and Groups for DB2

> Create Group

```bash
groupadd -g 1009 db2iadm1
groupadd -g 1008 db2fsdm1
groupadd -g 1007 dasadm1
```

> Create User

```bash
useradd db2inst1 -u 1004 -g db2iadm1 -m -d /home/db2inst1
useradd db2fenc1 -u 1003 -g db2fsdm1 -m -d /home/db2fenc1
useradd dasusr1 -u 1002 -g dasadm1 -m /home/dasusr1
```

> setting password for User

```bash
passwd db2inst1
passwd db2fenc1
passwd dasusr1
```

# STEP2  edit /etc/selinux/config and update SELINUX=disabled and Reboot


```bash
vi /etc/selinux/config
```

> config

```bash
SELINUX=disabled
```

> reboot the server

```bash
reboot
```


# STEP3 install packages to install DB2 

```bash
yum install libstdc++.i686 -y
yum install pam.i686 -y
yum install gcc-c++ -y
yum install ksh -y
yum install perl-Sys-Syslog.x86_64 -y
yum install sg3_utils -y
yum install patch -y
yum install kernel-devel -y
```

# STEP4 unzip or untar DB2 Install file on /[The place that you want to install]

```bash
tar xvf v10.5fp4_linuxx64_server.tar.gz /[The place You want to install]
```

# STEP5 run precheck 

```bash
./db2prereqcheck -v 10.5.0.0
```

# STEP6 DB2 install 

```
[root@hpjc06 disk1]# ./db2_install
DBI1324W Support of the db2_install command is deprecated. For
more information, see the DB2 Information Center.

Default directory for installation of products - /opt/ibm/db2/V10.5

***********************************************************
Install into default directory (/opt/ibm/db2/V10.5) ? [yes/no]
no
Enter the full path of the base installation directory:

------------------------------------------------
/inst/ibm/db2/dev/10.5


Specify one of the following keywords to install DB2 products.

SERVER
CONSV
EXP
CLIENT
RTCL

Enter "help" to redisplay product names.

Enter "quit" to exit.

***********************************************************
SERVER
***********************************************************
Do you want to install the DB2 pureScale Feature? [yes/no]
no
DB2 installation is being initialized.

Total number of tasks to be performed: 47
Total estimated time for all tasks to be performed: 1561 second(s)

Task #1 start
Description: Checking license agreement acceptance
Estimated time 1 second(s)
Task #1 end

Task #2 start
Description: Base Client Support for installation with root privileges
Estimated time 3 second(s)
Task #2 end

Task #3 start
Description: Product Messages - English
Estimated time 13 second(s)
Task #3 end

Task #4 start
Description: Base client support
Estimated time 293 second(s)
Task #4 end

Task #5 start
Description: Java Runtime Support
Estimated time 155 second(s)
Task #5 end

Task #6 start
Description: Java Help (HTML) - English
Estimated time 7 second(s)
Task #6 end

Task #7 start
Description: Base server support for installation with root privileges
Estimated time 7 second(s)
Task #7 end

Task #8 start
Description: Global Secure ToolKit
Estimated time 59 second(s)
Task #8 end

Task #9 start
Description: Java support
Estimated time 12 second(s)
Task #9 end

Task #10 start
Description: SQL procedures
Estimated time 3 second(s)
Task #10 end

Task #11 start
Description: ICU Utilities
Estimated time 35 second(s)
Task #11 end

Task #12 start
Description: Java Common files
Estimated time 18 second(s)
Task #12 end

Task #13 start
Description: Base server support
Estimated time 459 second(s)
Task #13 end

Task #14 start
Description: Control Center Help (HTML) - English
Estimated time 13 second(s)
Task #14 end

Task #15 start
Description: Connect support
Estimated time 3 second(s)
Task #15 end

Task #16 start
Description: Relational wrappers common
Estimated time 3 second(s)
Task #16 end

Task #17 start
Description: DB2 data source support
Estimated time 6 second(s)
Task #17 end

Task #18 start
Description: Spatial Extender server support
Estimated time 19 second(s)
Task #18 end

Task #19 start
Description: IBM Software Development Kit (SDK) for Java(TM)
Estimated time 48 second(s)
Task #19 end

Task #20 start
Description: DB2 LDAP support
Estimated time 4 second(s)
Task #20 end

Task #21 start
Description: DB2 Instance Setup wizard
Estimated time 20 second(s)
Task #21 end

Task #22 start
Description: Integrated Flash Copy Support
Estimated time 3 second(s)
Task #22 end

Task #23 start
Description: Spatial Extender client
Estimated time 3 second(s)
Task #23 end

Task #24 start
Description: Communication support - TCP/IP
Estimated time 3 second(s)
Task #24 end

Task #25 start
Description: Base application development tools
Estimated time 35 second(s)
Task #25 end

Task #26 start
Description: DB2 Update Service
Estimated time 4 second(s)
Task #26 end

Task #27 start
Description: Parallel Extension
Estimated time 3 second(s)
Task #27 end

Task #28 start
Description: EnterpriseDB code
Estimated time 4 second(s)
Task #28 end

Task #29 start
Description: Replication tools
Estimated time 53 second(s)
Task #29 end

Task #30 start
Description: Sample database source
Estimated time 4 second(s)
Task #30 end

Task #31 start
Description: itlm
Estimated time 3 second(s)
Task #31 end

Task #32 start
Description: DB2 Text Search
Estimated time 119 second(s)
Task #32 end

Task #33 start
Description: Command Line Processor Plus
Estimated time 4 second(s)
Task #33 end

Task #34 start
Description: Informix data source support
Estimated time 4 second(s)
Task #34 end

Task #35 start
Description: Oracle data source support
Estimated time 4 second(s)
Task #35 end

Task #36 start
Description: First Steps
Estimated time 3 second(s)
Task #36 end

Task #37 start
Description: Product Signature for DB2 Enterprise Server Edition
Estimated time 6 second(s)
Task #37 end

Task #38 start
Description: Guardium Installation Manager Client
Estimated time 20 second(s)
Task #38 end

Task #39 start
Description: Setting DB2 library path
Estimated time 180 second(s)
Task #39 end

Task #40 start
Description: Installing or updating DB2 HA scripts for IBM Tivoli System Automation for Multiplatforms (Tivoli SA MP)
Estimated time 40 second(s)
Task #40 end

Task #41 start
Description: Executing control tasks
Estimated time 20 second(s)
Task #41 end

Task #42 start
Description: Updating global registry
Estimated time 20 second(s)
Task #42 end

Task #43 start
Description: Starting DB2 Fault Monitor
Estimated time 10 second(s)
Task #43 end

Task #44 start
Description: Updating the db2ls link
Estimated time 1 second(s)
Task #44 end

Task #45 start
Description: Registering DB2 licenses
Estimated time 5 second(s)
Task #45 end

Task #46 start
Description: Setting default global profile registry variables
Estimated time 1 second(s)
Task #46 end

Task #47 start
Description: Initializing instance list
Estimated time 5 second(s)
Task #47 end

Task #48 start
Description: Registering DB2 Update Service
Estimated time 30 second(s)
Task #48 end

Task #49 start
Description: Updating global profile registry
Estimated time 3 second(s)
Task #49 end

The execution completed successfully.

For more information see the DB2 installation log at
"/tmp/db2_install.log.6265".

10) List the  newly installed db2copy.

[db2inst1@hpjc06 ~]$ db2ls

Install Path                       Level   Fix Pack   Special Install Number   Install Date                  Installer UID
---------------------------------------------------------------------------------------------------------------------
/opt/ibm/db2/V10.5              10.5.0.10       10                            Wed Nov 21 17:07:12 2018 EET             0
```

# STEP6 Create DAS

```bash
db2inst1@hpjc06:~# cd /opt/ibm/db2/V10.1/instance/
db2inst1@hpjc06:/opt/ibm/db2/V10.1/instance# pwd
/opt/ibm/db2/V10.1/instance
db2inst1@hpjc06:/opt/ibm/db2/V10.1/instance# ./dascrt -u dasusr1
SQL4406W  The DB2 Administration Server was started successfully.
DBI1070I  Program dascrt completed successfully.
```

# STEP7 Create Instance

```bash
db2inst1@hpjc06:/opt/ibm/db2/V10.1/instance# ./db2icrt -u db2fenc1 db2inst1
DBI1070I  Program db2icrt completed successfully.
```

# STEP8 Create the DB2 sample database to test

```bash
su - db2inst1
db2sampl
```
# STEP9 Test DB2 and access to the SAMPLE database

```bash
db2start
db2 connect to sample
db2 "select * from employee"
db2 connect reset
exit
```