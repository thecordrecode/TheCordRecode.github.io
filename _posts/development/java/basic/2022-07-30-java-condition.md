---
title: 자바-조건문
author: kimjeahyun
date: 2022-07-30 23:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 조건문

지금 까지 현재 배운 코딩은 절차지향의 형태로 진행되었다.
자바를 이용해 코딩을 하다보면 흐름을 바뀌는 형태가 많아지는데
그때 조건문을 사용한다.

사용자 로그인 기능 조건문 적용해보기
1. 입력한 아이디와 저장된 아이디가 일치하는지 확인한다.
   - 일치하지 않을 경우 실패 값을 반환한다.
2. 입력한 아이디가 저장된 아이디와 일치한다면 패스워드를 비교한다.
3. 입력한 패스워드가 저장된 패스워드와 일치한다면 로그인 성공 값을 반환한다.
   - 일치하지 않을 경우 실패 값을 반환한다.

로그인 로직을 구성하면 다음과 같이 조건값을 비교할텐데 이때 이용하는 것이 조건문이다.

<br>

# 문법

```java
if(조건식){
    //조건식이 참 일 떄 수행될 문장들을 적는다.
}
else if(조건식){

}
else{

}
```

<br>

# if문을 이용한 로그인 기능 구현

>login.java

```java
package conditionWhile;

public class login {
	
	String id = null;
	String passwd = null;
	
	public void storeAccount(String id,String passwd) {
		this.id = id;
		this.passwd = passwd;
	}
	
	public boolean Login(String id,String passwd) {
	
		boolean isok = false;
		
		if(this.id == id) {
			if(this.passwd == passwd) {
				isok = true;
				return isok;
			}
		}
		else {
			return isok;
		}
		
		return isok;
		
	}
	
}
```

>main.java

```java
package basic;

import conditionWhile.login;

public class main {
	public static void main(String[] args) {

		login lo = new login();
		lo.storeAccount("cordrecode", "good");
		
		if(lo.Login("cordrecode", "good")==true) System.out.println("로그인이 성공되었습니다.!");
	}
}

```

<br>

# switch 문

if문은 참과 거짓밖에 없기 때문에 경우의 수가 추가 될경우 else-if문을 계속해서 추가해야 한다. 그에 반해 switch 문은 하나의 조건문으로 여러개의 경우의 수를 처리 할 수 있다. 


```java
switch(조건식){
    case 값1:
        //문법
        break;
    case 값2:
        break;
    default:
}
```

switch 문을 이용하여 4칙연산 계산기 만들기.

>calc.class

```java
package conditionWhile;

public class calc {

	public int Calc(int number, char operator, int number2) {
		
		switch(operator) {
			case '*':
				return number * number2;
			case '+':
				return number + number2;
			case '-':
				return number - number2;
			case '/':
				return number / number2;
		}
		
		return 0;
	}
}

```

>main.class

```java
package basic;

import conditionWhile.calc;

public class main {
	public static void main(String[] args) {
		calc ca = new calc();
		System.out.println(ca.Calc(10, '+', 5));
		System.out.println(ca.Calc(10, '/', 5));
		System.out.println(ca.Calc(10, '-', 5));
		System.out.println(ca.Calc(10, '*', 5));
	}
}

```