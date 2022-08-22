---
title: MariaDB root 비밀번호 변경
author: kimjeahyun
date: 2022-08-22 12:00:00 +0900
categories: [DATABASE,MARIA]
tags: [DATABASE,MARIA]
---

# Mariadb root 비밀번호 변경

>Mariadb 계정 접속 

```sh
su - mariadb
```

>마리아디비 접속 및  스키마 연결

```sh
mysql
use mysql
```

>계정 정보 조회

```sql
SELECT HOST, USER,PASSWORD FROM WHERE WHERE = 'ID';
```

>패스워드 변경 및 FLUSH

```sql
SET PASSWORD FOR 'ID'@'HOST' = PASSWORD('NEW_PASSWORD');
FLUSH PRIVILEGES;
```



