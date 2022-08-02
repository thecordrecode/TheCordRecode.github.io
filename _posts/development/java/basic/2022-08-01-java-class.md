---
title: 자바-함수 및 클래스
author: kimjeahyun
<<<<<<<< HEAD:_posts/development/java/basic/x2022-08-02-java-class.md
date: 2022-08-02 22:00:00 +0900
========
date: 2022-08-01 17:00:00 +0900
>>>>>>>> 3d36183661fc83562132e3419ef7744675c8e4a3:_posts/development/java/basic/2022-08-01-java-class.md
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 함수

어떠한 작업을 수행할때 한곳에 집합되어 실행되는 코드

>함수를 사용하는 이유는?

- 재사용성이 높다.
- 중복된 코드를 제거 할수있다.
- 프로그램을 구조화 할수 있다.

선언방법

```java
반환타입 함수이름(타입 변수명, 타입 변수명...){
	//수행될 코드
}
```


# Class

지금까지 공부를 해오면서 알게 모르게 클래스를 살짝 살짝 보여드렸다.
클래스란 객체를 정의해놓은 것이며 객체의 설계도 또는 틀이라고 불리운다.
클래스는 객체지향 언어에서 중요한 부분에 속한다. 

자동차라는 객체를 만들때 만약에 자동차 설계도가 존재하지 않는다면 어떨까?
생성도중 균일하지 않은 오류가 발생 할것이고 1개를 완성하였다 치더라도 다시 만들때 설계도가 존재하지 않으니 또 다시 시련을 반복할 것이다.

마찬가지로 프래그래밍도 클래스라는 설계도가 존재하지 않는다면.
코드의 재사용성이 떨어질 것이며, 코드의 관리가 용이하지않고,균일하지 않은 오류가 발생하여 신뢰성이 떨어지게 될것이다.

> 클래스 정리

- 클래스란 객체를 정의해 놓은 것이다.
- 클래스는 객체를 생성하는데(인스턴스) 사용된다.

> 클래스의 구성요소는?

-   속성 필드,상태,특성
-   기능 메서드,함수,행위

>클래스 선언 방법

```java
class Person
{
    int age; //인스턴스 변수 
    static int variable; //클래스변수

    void method(){
        int number; //지역변수
    }
}
```

|변수의 종류|선언위치|생성시기|
|:--------:|:-----:|:------:|
|클래스변수|클래스 영역|클래스가 메모리에 올라갈 떄|
|인스턴스변수|클래스 영역|인스턴스가 생성되었을 때|
|지역변수|클래스 영역 이외의 영역|변수 선언문이 수행되었을 떄|

> 인스턴스 변수

클래스 영역에 생성되며 인스터스화 진행후 생성된 객체를 통해 접근할 수 있다. 또한 객체별로 다른값을 가질수 있다.

> 클래스 변수

인스턴스 변수와는 다르게 공통된 값을 가진다. 전역변수의 특징을 가진다.

> 지역 변수

메서드 내에 선언되면 메서드가 완료되면 사라진다. 

<br>

# 다시 한번 상기하자 인스턴스 

설계도를 통해서 객체를 생성하는 것을 인스턴스라 한다.

```java
package conditionWhile;

public class Person {

	//인스턴스 변수
	String name;
	int age;
	
	void introduce() {
		System.out.println("My name is "+name);
	}
	
}

```

```java
package basic;

import conditionWhile.Person;

public class main {
	public static void main(String[] args) {
		//인스턴스 설계도를 이용하여 객체를 생성
		Person person = new Person();
        person.name = "김재현";
	}
}

```

> person.name 여기서 볼수 있듯이
인스턴스 참조변수를 통해서만 다룰 수 있다
참조변수의 타입은 인스턴스의 타입과 같아야 한다.

<br>


# 생성자(Constructor)

생성자는 인스턴스가 진행되면서 처음으로 호출되는 초기화 함수이다.
보통의 경우 인스턴스 초기화의 주로 사용된다. 물론 명시적 초기화를 진행하는 것이 제일 좋다.

생성자는 생성될 경우 두가지를 주의 해야한다.
-	생성자의 이름은 클래스의 이름과 같아야 합니다.
-	생성자는 리턴 값이 없습니다.(초기화 목적)

```java
package conditionWhile;

public class Person {

	//인스턴스 변수
	String name = "김재현"; //명시적 초기화.
	int age;
	
	static String good = "good"; // 클래스 초기화
	
	{
		this.age=28; //인스턴스 초기화.
	}
	
	Person(String name,int age){
		//생성자 초기화
		this.name = name; 
		this.age = age;
	}
	
	void introduce() {
		System.out.println("My name is "+name);
	}
	
}

```