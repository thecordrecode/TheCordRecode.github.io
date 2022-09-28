---
title: MariaDB 유저생성
author: kimjeahyun
date: 2022-09-28 16:00:00 +0900
categories: [DATABASE,MARIA]
tags: [DATABASE,MARIA]
---


# Today I'll study about what you create a user of database 


# CREATE USER

Syntax

```sql
CREATE [OR REPLACE] USER [IF NOT EXISTS] 
 user_specification [,user_specification ...] 
  [REQUIRE {NONE | tls_option [[AND] tls_option ...] }]
  [WITH resource_option [resource_option ...] ]
  [lock_option] [password_option] 

user_specification:
  username [authentication_option]

authentication_option:
  IDENTIFIED BY 'password' 
  | IDENTIFIED BY PASSWORD 'password_hash'
  | IDENTIFIED {VIA|WITH} authentication_rule [OR authentication_rule  ...]

authentication_rule:
    authentication_plugin
  | authentication_plugin {USING|AS} 'authentication_string'
  | authentication_plugin {USING|AS} PASSWORD('password')

tls_option:
  SSL 
  | X509
  | CIPHER 'cipher'
  | ISSUER 'issuer'
  | SUBJECT 'subject'

resource_option:
  MAX_QUERIES_PER_HOUR count
  | MAX_UPDATES_PER_HOUR count
  | MAX_CONNECTIONS_PER_HOUR count
  | MAX_USER_CONNECTIONS count
  | MAX_STATEMENT_TIME time

password_option:
  PASSWORD EXPIRE
  | PASSWORD EXPIRE DEFAULT
  | PASSWORD EXPIRE NEVER
  | PASSWORD EXPIRE INTERVAL N DAY

lock_option:
    ACCOUNT LOCK
  | ACCOUNT UNLOCK
}
```

The CREATE USER statement creates new MariaDB accounts. 
To use it, You must have the global CREATE USER privilege or the INSERT privilege for the mysql database.

For each account, CREATE USER creates a new row in mysql.user 
if any of the specified accounts, or any permissions for the specified accounts,
already exits, then the server return ERROR 1396 
if an error occurs, CREATE USER will still create the accounts that do not result in an error.
Only one error is produced for all users which have not been created.

# OR REPLACE

if the optional OR REPLACE clause is used it is basically a shortcut for:

```sql
DROP USER IF EXISTS name;
CREATE USER name...;
```

For example:

```sql
CREATE USER foo2@test IDENTIFIED BY 'password';
ERROR 1396 (HY000): Operation CREATE USER failed for 'foo2'@'test'

CREATE OR REPLACE USER foo2@test IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)
```

# IF NOT EXISTS

When the IF NOT EXISTS clause is used, MariaDB will return a warning instead of an error 
if the specified user already exits.

```sql
CREATE USER foo2@test IDENTIFIED BY 'password';
ERROR 1396 (HY000): Operation CREATE USER failed for 'foo2'@'test'

CREATE USER IF NOT EXISTS foo2@test IDENTIFIED BY 'password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

SHOW WARNINGS;
+-------+------+----------------------------------------------------+
| Level | Code | Message                                            |
+-------+------+----------------------------------------------------+
| Note  | 1973 | Can't create user 'foo2'@'test'; it already exists |
+-------+------+----------------------------------------------------+
```

# Authentication Options

IDENTIFIED BY 'password'

The optional IDENTIFED BY clause can be used to provide an account with a password.
The password should be specified in plain text. it will be hashed by the PASSWORD function prior to being stored in the table.

For example , if our password is mariadb, then we can create the user with:

```sql
CREATE USER foo2@test IDENTIFIED BY 'mariadb';
```

If you do not specify a password with the IDENTIFIED BY clause, the user will be able to connect witout a password. A blank password is not a wildcard to match any password.
The user must connect without providing a password if no password is set.

# IDENTIFIED BY PASSWORD password_hash

The optional IDENTIFED BY PASSWORD clause can be used to provide an account with a password that has already been hashed. The password should be specified as a hash that was provided by the PASSWORD function. it will be stored in the table.

```sql
SELECT PASSWORD('mariadb');
+-------------------------------------------+
| PASSWORD('mariadb')                       |
+-------------------------------------------+
| *54958E764CE10E50764C2EECBB71D01F08549980 |
+-------------------------------------------+
1 row in set (0.00 sec)
```

