---
title: 자바-다형성
author: kimjeahyun
date: 2022-08-06 20:00:00 +0900
categories: [Languages for development,Java]
tags: [Languages for development,Java]
---

# 다형성(polymorphism)

객체지향개념에서 다형성이란 여러 가지 형태를 가질 수 있는 능력을 의미하며, 자바에서는 한 타입의 참조변수로 여러 타입의 객체를 참조할 수 있다. 

> 조상클래스 타입의 참조변수로 자손클래스의 인스턴스를 참조할 수 있도록 하였다는 것이다.


```java

class Tv{
    boolean power;
    int channel;
    
    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class smallTv extends Tv{
    String text;
    void caption(){/**/}
}

```
```java
smallTv c = new smallTv();
Tv t = new smallTv();
```

> 참조변수가 사용할 수 있는 맴버의 개수는 인스턴스의 맴버 개수보다 같거나 적어야 한다. !!

<br>

# 참조변수의 형변환

기본형 변수와 같이 참조변수도 형변환이 가능하다. 
> 단 서로 상속관계에 있는 클래스 사이에서만 가능하다.

-   자손타입 -> 조상타입 : 형변환 생략가능
-   조상타입 -> 자손타입 : 형변환 생략불가


# instanceof 연산자

참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기위해 사용된다.

```java
void doWork(Car c){
    if(c instanceof FireEngine){
        FireEngine fe = (FireEngine)c;
        fe.water();
    }
}
```

<br>

# 다형성 이용시 주의사항

-   맴버변수가 조상 클래스와 자손 클래스에 중복으로 정의된 경우, 조상타입의 참조변수를 사용했을 때는 조상클래스에 선언된 맴버변수가 사용된다.
-   중복 정의되지 않은 경우, 조상 타입의 참조변수를 사용했을 때와 자손타입의 참조변수를 사용했을 때의 차이는 없다.

<br>

# 매개변수의 다형성

참조변수의 다형적인 특징은 메서드의 매개변수에도 적용된다. 다른 객체가 3개가 존재할때. 상속받은 조상 클래스로 매개변수를 넘기면 한가지 타입으로 사용이 가능하다.

<br>

# 여러 종류의 객체를 배열로 다루기

조상클래스로 배열을 선언할 경우 그 조상클래스에 포함된 모든 객체를 담을수 있다.


