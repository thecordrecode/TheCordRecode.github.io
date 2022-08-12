---
title: MariaDB Install linux 에 설치하기 
author: kimjeahyun
date: 2022-08-11 20:00:00 +0900
categories: [설치,db]
tags: [설치,db]
---

# Mariadb 바이너리 설치하기

다음 예제는 /usr/local/mysql 폴더에 설치를 가정하고 마리아디비를 설치합니다.
물론 해당 디렉토리에만 설치를 해야 하는것은 아니다.

여기서 mysql은 폴더 자체로 하는것이 아니라. 심볼릭 링크를 통하여 설치를 
진행할 것이다. 이렇게 하면 버전을 변경할때 편하게 변경할수 있다.

>my.cnf 파일 확인하기!.

마리아 디비를 설치하기 전에 my.cnf 파일을 확인하여야 한다.
마리아 디비를 설치할때 my.cnf파일을 참조하는데 기본 위치는 /etc/my.cnf 이다.

# 마리아 디비 /usr/local/mysql 설치하기!

~~~
groupadd mysql
useradd -g mysql mysql
cd /usr/local
tar -zxvpf /path-to/mariadb-VERSION-OS.tar.gz
ln -s mariadb-VERSION-OS mysql
cd mysql
./scripts/mysql_install_db --user=mysql
chown -R root .
chown -R mysql data
~~~

마리아 디비 환경변수 설정하기

~~~
export PATH=$PATH:/usr/local/mysql/bin/
~~~

마리아 디비 실행하기

~~~
./bin/mysqld_safe --user=mysql &
or
./bin/mysqld_safe --defaults-file=~/.my.cnf --user=mysql &
~~~

서비스 등록하기

~~~
cp support-files/mysql.server /etc/init.d/mysql.server
cp support-files/systemd/mariadb.service /usr/lib/systemd/system/mariadb.service
mkdir /etc/systemd/system/mariadb.service.d/

cat > /etc/systemd/system/mariadb.service.d/datadir.conf <<EOF
[Service]
ReadWritePaths=/usr/local/mysql/data
EOF

systemctl daemon-reload
systenctl start mariadb.service
~~~