---
title: 자바-상속 과 오버라이딩
author: kimjeahyun
date: 2022-08-03 23:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 상속 interitance

상속이란 말 그대로 상속을 받는 다는 의미인데 Parent Class child Class 가 존재할때 parent 코드를 그대로 상속받아 child가 사용가능 하다고 생각하면 된다. 

Parent 와 child은 서로 상속관계가 있다 표현하며 parent 를 조상클래스 child 클래스를 자손클래스라고 칭한다.

상속계층도

![상속계층도](../../img/cpp/inheritance.png)

상속계층도에 보는것 과같이 parent 클래스는 child 클래스를 일부분 공유함을 볼수 있다. 따라서 child 함수가 추가 되어도 parent 클래스는 영향을 받지 않는다.

> 주의!: 생성자와 초기화 블럭은 상속되지 않습니다. 맴버만 상속됩니다.

> 주의!: 자손 클래스의 맴버 개수는 조상 클래스보다 항상 같거나 많습니다.

<br>

# 클래스의 재사용

-	상속
-	포함관계

> 포함 관계란?

클래스 내부에 다른 클래스를 인스턴스 하여 사용하는것.

```java
class child{
	Parent ch = new Parent();
}
```

클래스의 재사용에 대해서 상속과 포함관계 두개가 있는데 그렇다면 무엇을 써야할까?

가지고 있다와 , ~ 이다로 표현 할수 있다.
리모콘은 Tv의 채널 조작기능을 가지고 있다.
리모콘은 Tv 이다 
리모콘은 채널 조작 기능을 가지고 있기 때문에 포함관계이다.
소형티비는 Tv이다. 다음 같은 경우는 말이 되기 때문에 소형티비는 Tv를 상속해야 된다.

> 간단한 커피머신 설계해보기

VenddingMachine.class 
기본 자판기 틀 클래스를 만든다.

```java
package conditionWhile;

import java.util.List;

public class VenddingMachine {
	
	List<drink> drinkList;

	public void FillDrink(List<drink> drinkList) {
		this.drinkList = drinkList;
	}

	public drink pick(String name) {
		
		for(drink item : drinkList) {
			if(item.getName().equals(name)) {
				if(item.getCount() == 0) return null;
				item.setCount(item.getCount() - 1);
				return item;
			}
		}
		
		return null;
	}
	
	public void showDrink() {
		for(drink item: drinkList) {
			System.out.println("이름:"+item.getName()+" 갯수:"+item.getCount()+" 가격:"+item.getPrice());
		}
	}
	
}


```

drink.class 어떠한 형태로 자판기에 적재 할것인지 형태를 정해준다.

```java
package conditionWhile;

public class drink {
	
	private String name;
	private int count;
	private int price;
	
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getCount() {
		return count;
	}
	public void setCount(int count) {
		this.count = count;
	}
	public int getPrice() {
		return price;
	}
	public void setPrice(int price) {
		this.price = price;
	}
	
	
}

```

coffeeMachine.class 커피머신 객체를 만들어준다.
자판기 기능과 차이가 없다면 veddingMachine 클래스를 사용하여도 되지만.
커피머신은 주문시 3초간의 딜레이가 있다는 가정하에 상속받아 커피머신을 작성할 것이다.

```java
package conditionWhile;

public class coffeeMachine extends VenddingMachine{

	public void order(String name) throws InterruptedException {
		System.out.println("커피가 추출중입니다. 대기해주세요.");
		Thread.sleep(3000);
		super.pick(name);
		
		System.out.println("커피가 나왔습니다.!");
	}
	
}

```

main.class
테스트 클래스

```java
package basic;

import java.util.ArrayList;
import java.util.List;

import conditionWhile.coffeeMachine;
import conditionWhile.drink;



public class main {
	public static void main(String[] args) throws InterruptedException {	
		coffeeMachine cM = new coffeeMachine();
	
		List<drink> listDrink = new ArrayList<drink>();
		drink dr = new drink();
		dr.setCount(3);
		dr.setName("밀크커피");
		dr.setPrice(800);
		
		listDrink.add(dr);
		cM.FillDrink(listDrink);
		cM.showDrink();
		
		cM.order(dr.getName());
		cM.showDrink();
		
	}
}

```

결과
```
 이름:밀크커피 갯수:3 가격:800
 커피가 추출중입니다. 대기해주세요.
 커피가 나왔습니다.!
 이름:밀크커피 갯수:2 가격:800
```

<br>

# 오버라이딩

부모의 함수를 재정의 하는 것이다.
따라서 이름이 같아야 하며, 매개변수가 같아야하고 반환타입이 같아야한다.

다음과 같이 정말 간단한 클래스가 있다고 치자.

```java
package conditionWhile;

public class moving {
	
	public void run() {
		System.out.println("5의 속도로 뛰고 있습니다.");
	}

	public void walk() {
		System.out.println("2의 속도로 걷고 있습니다.");
	}
}
```


```java
package conditionWhile;

public class Person extends moving{

	public void walk() {
		System.out.println("3의 속도로 걷고있습니다.");
	}
	
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

사람 클래스에 moving 상속을 받아 walk 라는 함수를 오버라이딩 하였다.
동물 사람 다양한 동물들의 걷고 뛰는 행동은 동일 하지만 속도는 다를 것이다. 이렇듯이 내가 필요한 함수를 상속받은 위치에서 재정의 하는것을 오버라이딩 이라고 한다.

