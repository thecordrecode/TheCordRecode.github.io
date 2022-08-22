---
title: MariaDB 기초모음 
author: kimjeahyun
date: 2022-08-22 12:00:00 +0900
categories: [DATABASE,MARIA]
tags: [DATABASE,MARIA]
---


# 마리아 디비 로그인

```Shell
mysql -u root -p -h localhost
```

>데이터베이스 생성

```SQL
CREATE DATABASE bookstore;

USE bookstore;
```

>테이블 생성

```SQL
CREATE TABLE books (
isbn CHAR(20) PRIMARY KEY, 
title VARCHAR(50),
author_id INT,
publisher_id INT,
year_pub CHAR(4),
description TEXT );
```

>데이터 넣기

```SQL
INSERT INTO books
(title, author_id, isbn, year_pub)
VALUES('The Castle', '1', '0805211063', '1998');
```

>데이터 조회

```SQL
SELECT title 
FROM books;
```