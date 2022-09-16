---
title: jboss install on the linux
author: kimjeahyun
date: 2022-09-16 00:00:00 +0900
categories: [설치,was]
tags: [설치,was]
---

# jboss 설치

jboss를 설치하는 방법은 두가지로 나뉜다.

-   zip 파일
-   rpm packages

이 장에서는 zip파일로 설치하는 방법에대해 기술한다.

# 전제조건

jboss를 설치하기 위해서는 os에 java가 설치되어 있어야 한다.

[JBoss Web Server 5 Supported Configurations.](https://access.redhat.com/articles/3497401/) 다음 URL를 통하여 jboss와 jdk 호환성 정보를 볼 수 있다.
자기가 설치할 jboss 버전에 따라 jdk를 설치 해야 한다.

[자바 설치하기](https://thecordrecode.github.io/posts/install-os-linux-java/) 

# jboss web application server install 

1. jboss 홈페이지 로그인 [Red Hat Customer Portal](https://access.redhat.com/)

2. Downloads 클릭
3. Red Hat Jboss Web Server 클릭
4. jboss download

# jboss 계정 생성

~~~
useradd jboss
~~~

# java version check

~~~
java -version
~~~

# 압축 풀기 

~~~
unzip jboss-eap-6.4.0.zip
~~~

# jboss 실행하기

~~~
sh /home/jboss/jboss-eap-6.4/bin/standalone.sh
~~~

# 외부 접속시 다음 환경파일 수정 필요

vi /home/jboss/jboss-eap-6.4/standalone/configuration/standalone.xml


before
~~~

    <interfaces>
        <interface name="management">
            <inet-address value="${jboss.bind.address.management:127.0.0.1}"/>
        </interface>
        <interface name="public">
            <inet-address value="${jboss.bind.address:127.0.0.1}"/>
        </interface>
        <!-- TODO - only show this if the jacorb subsystem is added  -->
        <interface name="unsecure">
            <!--
              ~  Used for IIOP sockets in the standard configuration.
              ~                  To secure JacORB you need to setup SSL
              -->
            <inet-address value="${jboss.bind.address.unsecure:127.0.0.1}"/>
        </interface>
    </interfaces>

~~~

after

~~~
    <interfaces>
        <interface name="management">
            <inet-address value="${jboss.bind.address.management:0.0.0.0}"/>
        </interface>
        <interface name="public">
            <inet-address value="${jboss.bind.address:0.0.0.0}"/>
        </interface>
        <!-- TODO - only show this if the jacorb subsystem is added  -->
        <interface name="unsecure">
            <!--
              ~  Used for IIOP sockets in the standard configuration.
              ~                  To secure JacORB you need to setup SSL
              -->
            <inet-address value="${jboss.bind.address.unsecure:0.0.0.0}"/>
        </interface>
    </interfaces>
~~~



해당 주소로 열어보기

http://localhost:8080/