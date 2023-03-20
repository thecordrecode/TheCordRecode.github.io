---
title: 자바-제어자
author: kimjeahyun
date: 2022-08-04 20:10:00 +0900
categories: [Languages for development,Java]
tags: [Languages for development,Java]
---

# this , super

>this 인스턴스 자신을 가리키는 참조변수, 인스턴스의 주소가 저장되어 있다. 

>super 조상 클래스의로부터 상속받은 맴버를 참조하는데 사용한다.

<br>

# 제어자(modifier)

메서드의 선언부에 함께 사용되어 부가적인 의미를 부여한다.

종류

-   public
-   protected
-   default
-   private
-   static
-   final
-   abstract
-   native
-   transient
-   synchronzied
-   volatile
-   strictfp

# static

인스턴스 없이 사용가능하며 호출이 매우 편리하고 속도도 빠르다.

# final

변경이 될수 없는 상수의 의미를 가진다.

# abstract

추상클래스를 선언할때 사용한다.

# 접근제어자

public > protected > default > private

-   public 접근제한이 없다.
-   private 같은 클래스 내에서만 사용 가능
-   default 패키지내의 클래스만 접근 가능하다.
-   protected 패키지에 관계없이 상속관계에 있는 자손클래스가 접근 가능.


> 주의사항

-   메서드에 static과 abstract를 함께 사용할 수 없다.
-   클래스에 abstract와 final을 동시에 사용할 수 없다.
-   abstract메서드의 접근 제어자가 private일 수 있다.
-   메서드에 private과 final을 같이 사용할 필요는 없다.

