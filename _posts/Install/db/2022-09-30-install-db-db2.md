---
title: DB2 server install
author: kimjeahyun
date: 2022-09-30 00:00:00 +0900
categories: [설치,db]
tags: [설치,db]
---

# Before you begin

- If you are planning on setting up a partitioned database environment, refer to the task in the related links.

- Ensure that your system meets installation, memory, and disk requirements.

- Ensure that your installed a supported browser.

- You can install a DB2 database server by using either root or non-root authority. For more information about non-root installation , see the related links

- The DB2 database product image must be available. You can obtain a DB2 installation image either by purchasing a physical DB2 database product DVD or by downloading an installation image from Passport Advantage.

- If you are installing a non-English version of a DB2 database product, you must have the appropriate national Language Package.

- The DB2 Setup wizard is a graphical installer. To install a DB2 product by using the DB2 Setup wizard, you require an X Window System(x11) to display the graphical user interface (GUI) . To display the GUI on your local workstation , the X Window System software must be installed and running you must also set the DISPLAY variable to the IP address of the workstation you use to install the DB2 product:

# 

~~~
sudo yum install libstdc++.i686 -y

sudo yum install pam.i686 -y

sudo yum install gcc-c++ -y

sudo yum install ksh -y

sudo yum install perl-Sys-Syslog.x86_64 -y

yum install kernel-devel -y
~~~