---
title: WebLogic 14.1.1.0 Install linux 에 설치하기 
author: kimjeahyun
date: 2022-08-11 20:00:00 +0900
categories: [설치,was]
tags: [설치,was]
---

# 전제조건 

-   Java SE8 


# 계정과 유저 생성하기

>명령어

~~~
groupadd -g 1200 weblogic
useradd -u 1100 -g weblogic weblogic
passwd weblogic
~~~

>출력화면

~~~
[root@localhost ~]# groupadd -g 1200 weblogic
[root@localhost ~]# useradd -u 1100 -g weblogic weblogic
[root@localhost ~]# passwd weblogic
Changing password for user weblogic.
New password:
BAD PASSWORD: The password fails the dictionary check - it is too simplistic/systematic
Retype new password:
passwd: all authentication tokens updated successfully.
~~~

>weblogic 설치될 디렉토리 생성 및 권한 부여

~~~
mkdir -p /app/weblogic/middleware
mkdir -p /app/weblogic/config/domains
mkdir -p /app/weblogic/config/applications
mkdir -p /app/weblogic/oraInventory
chown -R weblogic:weblogic /app
chmod -R 775 /app/
~~~

mkdir 

 -p 디렉토리가 없을경우 자동으로 상위 부모 디렉토리까지 자동으로 생성해준다. 

chmod , chown 

-R 하위디렉토리까지 적용한다.


weblogic 환경변수 셋팅하기.

>환경변수 파일 위치 

/home/weblogic/.bash_profile

~~~
export MW_HOME=/app/weblogic/middleware
export WLS_HOME=$MW_HOME/wlserver
export WL_HOME=$WLS_HOME
# Set to the appropriate JAVA_HOME.
export JAVA_HOME=/etc/jdk/jdk1.8.0_331
export PATH=$JAVA_HOME/bin:$PATH
~~~

~~~
source .bash_profile
~~~

>설정파일 생성하기

~~~
touch /app/weblogic/config/applications/wls.rsp
touch /app/weblogic/config/applications/fmw_infr.rsp
touch /app/weblogic/config/applications/oraInst.loc
~~~

>wls.rsp

~~~
[ENGINE]
Response File Version=1.0.0.0.0
[GENERIC]
ORACLE_HOME=/app/weblogic/middleware
INSTALL_TYPE=WebLogic Server
MYORACLESUPPORT_USERNAME=
MYORACLESUPPORT_PASSWORD=<SECURE VALUE>
DECLINE_SECURITY_UPDATES=true
SECURITY_UPDATES_VIA_MYORACLESUPPORT=false
PROXY_HOST=
PROXY_PORT=
PROXY_USER=
PROXY_PWD=<SECURE VALUE>
COLLECTOR_SUPPORTHUB_URL=
~~~

>fmw_infr.rsp

~~~
[ENGINE]
Response File Version=1.0.0.0.0
[GENERIC]
ORACLE_HOME=/app/weblogic/middleware
INSTALL_TYPE=Fusion Middleware Infrastructure
MYORACLESUPPORT_USERNAME=
MYORACLESUPPORT_PASSWORD=<SECURE VALUE>
DECLINE_SECURITY_UPDATES=true
SECURITY_UPDATES_VIA_MYORACLESUPPORT=false
PROXY_HOST=
PROXY_PORT=
PROXY_USER=
PROXY_PWD=<SECURE VALUE>
COLLECTOR_SUPPORTHUB_URL=
~~~

>oraInst.loc

~~~
inventory_loc=/app/weblogic/oraInventory
inst_group=weblogic
~~~

>설치

~~~
$JAVA_HOME/bin/java -Xmx1024m -jar /home/weblogic/fmw_14.1.1.0.0_wls_lite_generic.jar -silent -responseFile /app/weblogic/config/applications/wls.rsp -invPtrLoc /app/weblogic/config/applications/oraInst.loc
~~~

>WLST 방식 domain 생성하기 

~~~
sh /app/weblogic/middleware/wlserver/common/bin/wlst.sh


wls:/offline> readTemplate('/app/weblogic/middleware/wlserver/common/templates/wls/wls.jar')
wls:/offline/base_domain>cd('Servers/AdminServer')
wls:/offline/base_domain/Server/AdminServer>set('ListenAddress','')
wls:/offline/base_domain/Server/AdminServer>set('ListenPort', 7001)
wls:/offline/base_domain/Server/AdminServer>create('AdminServer','SSL')
Proxy for AdminServer: Name=AdminServer, Type=SSL
wls:/offline/base_domain/Server/AdminServer>cd('SSL/AdminServer')
wls:/offline/base_domain/Server/AdminServer/SSL/AdminServer>set('Enabled', 'True')
wls:/offline/base_domain/Server/AdminServer/SSL/AdminServer>set('ListenPort', 7002)
wls:/offline/base_domain/Server/AdminServer/SSL/AdminServer>cd('/')
wls:/offline/base_domain>cd('Security/base_domain/User/weblogic')
wls:/offline/base_domain/Security/base_domain/User/weblogic>cmo.setPassword('weblogic1')
wls:/offline/base_domain/Security/base_domain/User/weblogic>setOption('OverwriteDomain', 'true')
wls:/offline/base_domain/Security/base_domain/User/weblogic>writeDomain('/app/weblogic/middleware/user_projects/domains/server')

closeTemplate()
exit()
~~~

>weblogic 실행

~~~
sh /app/weblogic/middleware/user_projects/domains/server/bin/startWebLogic.sh  &
sh /app/weblogic/middleware/user_projects/domains/server/bin/startNodeManager.sh &
~~~


http://ip:7001/console 을 접속하여 테스트