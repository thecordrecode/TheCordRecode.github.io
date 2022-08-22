---
title: MariaDB 기초모음 
author: kimjeahyun
date: 2022-08-22 12:00:00 +0900
categories: [DATABASE,MARIA]
tags: [DATABASE,MARIA]
---


# 마리아 디비 로그인

```sh
mysql -u root -p -h localhost
```

>데이터베이스 생성

```mysql
CREATE DATABASE bookstore;

USE bookstore;
```

>테이블 생성

```mysql
CREATE TABLE books (
isbn CHAR(20) PRIMARY KEY, 
title VARCHAR(50),
author_id INT,
publisher_id INT,
year_pub CHAR(4),
description TEXT );
```

>데이터 넣기

```mysql
INSERT INTO books
(title, author_id, isbn, year_pub)
VALUES('The Castle', '1', '0805211063', '1998');
```

>데이터 조회

```mysql
SELECT title 
FROM books;
```

>데이터베이스 및 유저 생성

```mysql
-- database 생성(mysqladmin이용)
C:\>mysqladmin -uroot -p create scott

-- database 생성(root유저로 접속)
C:\mysql\bin>mysql -uroot -pstorm mysql

-- database 삭제
mysql> drop database scott;

-- database 생성
mysql> CREATE DATABASE scott;

-- user생성
mysql>insert into user (host,user,password) values('localhost','scott',password('tiger'));
mysql>insert into db values('localhost','scott','scott','y','y','y','y','y','y','y','y','y','y','y','y');

-- 변경사항 적용
mysql>flush privileges;

-- user삭제
mysql>DELETE FROM user WHERE user='scott' AND host='localhost';

-- 변경사항 적용
mysql>flush privileges; 

-- grant문을 이용해서 사용자를 추가하는 방법
mysql>grant all on scott.* to scott@'localhost' identified by 'tiger'; 

-- 새로만든 scott db에 scott유저로 접속
C:\mysql\bin>mysql -uscott -ptiger scott

-- script파일 실행(Oracle :start, @)
mysql>source C:\scott.sql

```


>로우 제한

```mysql
-- 앞에서 3개의 데이터를 조회함
mysql>SELECT empno, ename FROM emp LIMIT 3;

-- 2번째 이후의 데이터-부터 2개의 데이터를 조회함
mysql>SELECT empno, ename FROM emp LIMIT 2,2;
```