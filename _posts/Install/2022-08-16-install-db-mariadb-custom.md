---
title: MariaDB Install linux 커스텀하여 설치하기 
author: kimjeahyun
date: 2022-08-16 17:00:00 +0900
categories: [설치,db]
tags: [설치,db]
---

# Mariadb 바이너리 설치하기

다음 예제는 커스텀마이징 하여 마리아디비를 설치합니다.

또한 mysql은 폴더 자체로 하는것이 아니라. 심볼릭 링크를 통하여 설치를 
진행할 것이다. 이렇게 하면 버전을 변경할때 편하게 변경할수 있다.

>my.cnf 파일 확인하기!.

마리아 디비를 설치하기 전에 my.cnf 파일을 확인하여야 한다.
마리아 디비를 설치할때 my.cnf파일을 참조하는데 기본 위치는 /etc/my.cnf 이다.

# 마리아 디비 커스텀마이징하여 설치하기!

~~~
groupadd mysql
useradd -g mysql mysql
cd /home/mysql
tar -zxvpf /path-to/mariadb-VERSION-OS.tar.gz
ln -s mariadb-VERSION-OS mysql
~~~

> my.cnf 셋팅하기

~~~

[client-server]
# Uncomment these if you want to use a nonstandard connection to MariaDB
socket=/home/mysql/socket/mysql.sock
port=3306

# This will be passed to all MariaDB clients
[client]
password=wise1012

# The MariaDB server
[mysqld]
# Directory where you want to put your data
data=/home/mysql/mysql/data
# Directory for the errmsg.sys file in the language you want to use
language=/home/mysql/english

# This is the prefix name to be used for all log, error and replication files
log-basename=mysqld

# Enable logging by default to help find problems
# general-log
# log-slow-queries

~~~

마리아 디비 환경변수 설정하기

~~~
export PATH=$PATH:/home/mysql/mysql/bin/
~~~

마리아 디비 설치하기

~~~
./scripts/mysql_install_db --defaults-file=~/.my.cnf
~~~

마리아 디비 실행하기

~~~
./bin/mysqld_safe --defaults-file=~/.my.cnf &
~~~

마리아 디비 중지하기

~~~
mysqladmin shutdown
~~~

서비스 등록하기

~~~
cp support-files/systemd/mariadb.service /usr/lib/systemd/system/mariadb.service
mkdir /etc/systemd/system/mariadb.service.d/

cat > /etc/systemd/system/mariadb.service.d/datadir.conf <<EOF
[Service]
ReadWritePaths=/usr/local/mysql/data
EOF

systemctl daemon-reload
systemctl start mariadb.service
~~~


# 마리아 디비 유저 생성

~~~
CREATE USER '유저명'@localhost IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO '유저명'@localhost IDENTIFIED BY 'password';
~~~

그후 접속하면 끝