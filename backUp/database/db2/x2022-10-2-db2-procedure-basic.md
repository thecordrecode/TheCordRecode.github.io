---
title: DB2 procedure basic
author: kimjeahyun
date: 2022-10-02 12:00:00 +0900
categories: [DATABASE,DB2]
tags: [DATABASE,DB2]
---


# Stored procedure parameters

you can pass information between a stored and the calling application program by using parameters. Applications pass the required parameters in the SQL CALL statement. optionally, the application can also include an indicator variable with each parameter to allow for null values or to pass large output parameter values.

you define the stored procedure parameters as part of the stored procedure in the CREATE PROCEDURE statement. The stored procedure parameters can be one of the following types:

IN 

-   input-only parameters, which provide values to the stored procedure.

OUT

-   Output-only parameters. which return values from the stored procedure to the calling program.

INOUT

-   Input and output parameters. which provide values to and return values from stored procedure.


If a stored procedure fails to set one or more of the OUT or INOUT parameters, Db2 does not return an error. Instead, DB2 returns the output parameters to the calling program , with the values that were established on entry to the stored procedure.


# SQL procedure body

The body of an SQL procedure contains one or more SQL statements. In the SQL procedure body, you can also declare and use variables, conditions, return codes, statements, cursors, and handlers.


# TO INSERT DATA INTO TABLE

```sql

CREATE PROCEDURE EMP
(
    IN EMPNUMBER CHAR(6),
    IN NAME VARCHAR(50),
    IN SARALY INT 
)
BEGIN

    INSERT INTO EMP(EMPNUMBER,NAME,SARALY) VALUES(EMPNUMBER,NAME,SARALY);

END

```

# Excuting Procedure

```sql
CALL EMP('000001','김재현',1200);
```


# Change value

```sql
CREATE PROCEDURE UPDATE_SALARY_1
(
	IN EMPLOYEE_NUMBER CHAR(6),
	IN RATE DECIMAL(6,2)
)
LANGUAGE SQL
MODIFIES SQL DATA
DETERMINISTIC
COMMIT ON RETURN YES
	UPDATE EMP 
		SET EMP.SALARY = SALARY * RATE
		WHERE EMP.EMPNUMBER = EMPLOYEE_NUMBER

```

> LANGUAGE SQL

This clause is used to specify that the procedure body is written in the SQL Language.

> MODIFIES SQL DATA

Specified that the procedure can run any SQL statement except statements that are not supported in procedures

> DETERMINISTIC or not DETERMINISTIC

This clause specifies whether the procedure always returns the same results for given argument values (DETERMINISTIC) or whether the
procedure depends on some state values that affect the result (NOT DETERMINISTIC)

> COMMIT ON RETURN

Indicates whether a commit is to be issued on return from the procedure. The default is NO.



# Examples of SQL CASE


```sql

CREATE OR REPLACE PROCEDURE UPDATESALARY
(
	IN EMPNUMBER CHAR(6),
	IN RATING INT
)
LANGUAGE SQL 
MODIFIES SQL DATA 
	
CASE RATING
	 WHEN 1 THEN 
	 	UPDATE EMP 
	 		SET EMP.SALARY = SALARY * 1.10 WHERE EMP.EMPNUMBER = EMPNUMBER;
	 WHEN 2 THEN
	 	UPDATE EMP 
	 		SET EMP.SALARY = SALARY * 1.20 WHERE EMP.EMPNUMBER = EMPNUMBER;
	 WHEN 3 THEN
	 	DELETE FROM EMP WHERE EMP.EMPNUMBER = EMPNUMBER;

END CASE

```

> LANGUAGE SQL

This clause is used to specify that the procedure body is written in the SQL Language.

> MODIFIES SQL DATA

Specified that the procedure can run any SQL statement except statements that are not supported in procedures



# Example 

```sql


```

