---
title: MariaDB Drop table
author: kimjeahyun
date: 2022-09-28 16:00:00 +0900
categories: [DB,MARIA]
tags: [DB,MARIA]
---

# How to remove the table by executing sql syntax

Do you think about where is table list what we had made tables?

if you know that can you create the SQL clause?

first of all created table list is stored at the information_schema.tables


Drop syntax is under:

```sql
Drop table table_name;
```

if I want to delete the all table now can create Syntax through the next syntax

```sql
SELECT CONCAT('DROP TABLE IF EXISTS ',TABLE_NAME,';') FROM information_schema.tables
	WHERE TABLE_SCHEMA = 'SCHEMA_NAME';
```