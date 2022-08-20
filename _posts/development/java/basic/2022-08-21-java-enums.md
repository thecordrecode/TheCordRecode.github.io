---
title: 자바-열거형
author: kimjeahyun
date: 2022-08-21 13:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 열거형 enum

열거형이란 기존의 프로그램은 값만 같으면 논리식에서 TRUE를 반환한다.
열거형은 논리식 비교시 타입이랑 값까지 비교하여 논리적 오류를 줄인다.

다음은 열거형을 이용하여 각 디비별 jdbc, url , driver를 가져오는 열거형을 만들어보도록 하겠다.

```java
package enums;

enum Database{
	ORACLE,
	MARIA,
	MSSQL,
	TIBERO
}

enum Jdbc {

	JDBC("OracleJdbcSyntax","MariaJdbcSyntax","TiberoJdbcSyntax","MssqlJdbcSyntax"){
		String toString(Database database) {
			switch(database) {
			case ORACLE:
				return JDBC.getOracle();
			case MARIA:
				return JDBC.getMaria();
			case MSSQL:
				return JDBC.getMssql();
			case TIBERO:
				return JDBC.getTibero();
			}
			return Maria;
		}
	},
	URL("OracleURLSyntax","MariaURLSyntax","TiberoURLSyntax","MssqlURLSyntax"){
		String toString(Database database) {
			switch(database) {
			case ORACLE:
				return URL.getOracle();
			case MARIA:
				return URL.getMaria();
			case MSSQL:
				return URL.getMssql();
			case TIBERO:
				return URL.getTibero();
			}
			return Maria;
		}
	},
	Driver("OracleDriverSyntax","MariaDriverSyntax","TiberoDriverSyntax","MssqlDriverSyntax"){
		String toString(Database database) {
			switch(database) {
			case ORACLE:
				return Driver.getOracle();
			case MARIA:
				return Driver.getMaria();
			case MSSQL:
				return Driver.getMssql();
			case TIBERO:
				return Driver.getTibero();
			}
			return Maria;
		}
	};
	private static final Jdbc[] DIR_ARR = Jdbc.values();
	protected final String Oracle;
	protected final String Maria;
	protected final String Tibero;
	protected final String Mssql;
	
	Jdbc(String Oracle, String Maria, String Tibero, String Mssql) {
		this.Oracle = Oracle;
		this.Maria = Maria;
		this.Tibero = Tibero;
		this.Mssql = Mssql;
		// TODO Auto-generated constructor stub
	}
	
	String getOracle() {
		return this.Oracle;
	}
	String getMaria() {
		return this.Maria;
	}
	String getTibero() {
		return this.Tibero;
	}
	String getMssql() {
		return this.Mssql;
	}

	
	public static Jdbc of(int dir) {
		if(dir < 1 || dir > 4) {
			throw new IllegalArgumentException("Invalid value:"+dir);
		}
		return DIR_ARR[dir-1];
	}
	
	abstract String toString(Database dabase);

}

```

> main

```java
package enums;

public class main {

	public static void main(String[] args) {
		System.out.println(Jdbc.JDBC.toString(Database.ORACLE));
		System.out.println(Jdbc.JDBC.getOracle());
		System.out.println(Jdbc.JDBC.toString(Database.MSSQL));
		System.out.println(Jdbc.JDBC.getMssql());
		System.out.println(Jdbc.JDBC.toString(Database.MARIA));
		System.out.println(Jdbc.JDBC.getMaria());
		System.out.println(Jdbc.JDBC.toString(Database.MSSQL));
		System.out.println(Jdbc.JDBC.getMssql());
		
		System.out.println(Jdbc.URL.toString(Database.ORACLE));
		System.out.println(Jdbc.URL.getOracle());
		System.out.println(Jdbc.URL.toString(Database.MSSQL));
		System.out.println(Jdbc.URL.getMssql());
		System.out.println(Jdbc.URL.toString(Database.MARIA));
		System.out.println(Jdbc.URL.getMaria());
		System.out.println(Jdbc.URL.toString(Database.MSSQL));
		System.out.println(Jdbc.URL.getMssql());
		
		System.out.println(Jdbc.Driver.toString(Database.ORACLE));
		System.out.println(Jdbc.Driver.getOracle());
		System.out.println(Jdbc.Driver.toString(Database.MSSQL));
		System.out.println(Jdbc.Driver.getMssql());
		System.out.println(Jdbc.Driver.toString(Database.MARIA));
		System.out.println(Jdbc.Driver.getMaria());
		System.out.println(Jdbc.Driver.toString(Database.MSSQL));
		System.out.println(Jdbc.Driver.getMssql());

		
		System.out.println(Jdbc.of(1).getOracle());
		System.out.println(Jdbc.of(2).getOracle());
		System.out.println(Jdbc.of(3).getOracle());

	}
}

```

출력

~~~
OracleJdbcSyntax
OracleJdbcSyntax
MssqlJdbcSyntax
MssqlJdbcSyntax
MariaJdbcSyntax
MariaJdbcSyntax
MssqlJdbcSyntax
MssqlJdbcSyntax
OracleURLSyntax
OracleURLSyntax
MssqlURLSyntax
MssqlURLSyntax
MariaURLSyntax
MariaURLSyntax
MssqlURLSyntax
MssqlURLSyntax
OracleDriverSyntax
OracleDriverSyntax
MssqlDriverSyntax
MssqlDriverSyntax
MariaDriverSyntax
MariaDriverSyntax
MssqlDriverSyntax
MssqlDriverSyntax
OracleJdbcSyntax
OracleURLSyntax
OracleDriverSyntax
~~~