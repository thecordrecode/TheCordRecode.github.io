---
title: 자바-추상클래스 와 인터페이스
author: kimjeahyun
date: 2022-08-05 20:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 추상클래스(abstract class)

> 부분적 미완성의 설계도 이다.

미완성의 설계도는 왜 필요할까? 이전에 클래스의 경우 함수를 선언하면 반드시 구현까지 동시에 진행 하여야 했다. 이렇게 되면 구체적인 설계도를 구성하므로 설계도가 완성되기까지의 시간이 많이 소요될 뿐더러 좀더 추상적인 설계를 할수 없다. 때문에 자바에서는 추상 클래스라는 문법을 제공한다. 

추상클래스에서는 함수를 선언하고 구현은 하지 않는다. 따라서 추상적인 설계가 가능하다. 추상클래스는 공통적인 부분을 함수를 정의하고 상속을 통해서 오버라이딩을 통해 함수의 구현이 가능하다.

```java
package conditionWhile;

abstract public class aPerson {
	abstract void move();
}
```

```java
package conditionWhile;

public class GoodPerson extends aPerson{

	@Override
	void move() {
		System.out.println("TEST");
	}
	
}

```

여기서 알수 있는것은 추상클래스로 설계한것은 반드시 오버라이드를 통해 재정의를 하여야지만 사용이 가능하다는 점이다.

<br>

# 인터페이스

정말 밑그림만 그려진 기본 설계도라 표현 할 수 있다.


-   모든 맴버변수는 public static final 이어야 하며 생략 가능하다.
-   모드 메서드는 public abstract 이어야 하며 이를 생략 할 수 있다.

> 인터페이스는 다중 상속이 가능하다. 


인터페이스의 장점들

-   개발시간을 줄일 수 있다.
-   표준개발이 가능하다.
-   서로 관계없는 클래스들에게 관계를 맺어 줄 수 있다.
-   독립적인 프로그래밍이 가능하다.



<br>

인터페이스 예제

movin.interface

```java
package example4;

public interface moving {
	void run();
	void walk();
	
}
```

speak.interface

```java
package example4;

public interface speak {
	public void speak();
}

```

human.class

```java
package example4;

public class human implements moving{
	int age;
	String name;
	String gender;
	speak sp;
	public human(int age,String name,String gender){
		this.age = age;
		this.name = name;
		this.gender = gender;
		this.sp = (speak) this;
	}

	public void tell() {
		sp.speak();
	}
	
	@Override
	public void run() {
		// TODO Auto-generated method stub
		System.out.println("사람이 뛴다");
	}

	@Override
	public void walk() {
		// TODO Auto-generated method stub
		System.out.println("사람이 걷는다");
	}
}

```

man.class

```java
package example4;

public class man extends human implements speak{

	public man(int age, String name) {
		super(age, name, "남자");
		// TODO Auto-generated constructor stub
	}

	@Override
	public void speak() {
		// TODO Auto-generated method stub
		System.out.println("남자목소리!");
	}

}

```

woman.class

```java
package example4;

public class woman extends human implements speak{

	public woman(int age, String name) {
		super(age, name, "여성");
		// TODO Auto-generated constructor stub
	}

	@Override
	public void speak() {
		// TODO Auto-generated method stub
		System.out.println("여성 목소리");
	}

}

```

dog.class

```java
package example4;

public class dog implements speak,moving{

	@Override
	public void speak() {
		// TODO Auto-generated method stub
		System.out.println("멍멍");
	}

	@Override
	public void run() {
		// TODO Auto-generated method stub
		System.out.println("개가 뛴다");
	}

	@Override
	public void walk() {
		// TODO Auto-generated method stub
		System.out.println("개가 걷는다.");
	}

}

```

main.class

```java
package basic;

import example4.dog;
import example4.human;
import example4.man;
import example4.woman;

class main {
	public static void main(String[] args) {	
		human hu = new man(25,"남자1");
		human whu = new woman(25,"여자1");
		dog d = new dog();
		
		hu.tell();
		hu.run();
		hu.walk();
		whu.tell();
		whu.run();
		whu.walk();
		d.speak();
		d.run();
		d.walk();
		
	}
}

```

>출력결과

~~~
남자목소리!
사람이 뛴다
사람이 걷는다
여성 목소리
사람이 뛴다
사람이 걷는다
멍멍
개가 뛴다
개가 걷는다.
~~~

여기서 사람이 걷는것과 뛰는것은 여성과 남성을 공통의 같다는 전제하에 
코드를 짜보았다. 따라서 상속을 human 쪽에 받아 오버라이드를 정의하였다.

여성과 남성의 목소리는 차이점을 두었는데 때문에 인터페이스를 각각 성별에 따라 직접 할당 받아 오버라이드를 정의하여 상위 클래스인 인간 클래스에서 speak 함수를 호출함에 따라 코드 중복을 줄였다.

이처럼 인터페이스를 사용하면 코드를 획기적으로 줄 일 수 있다.