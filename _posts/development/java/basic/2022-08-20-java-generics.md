---
title: 자바-지네릭스
author: kimjeahyun
date: 2022-08-20 13:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 지네릭스

지네릭스는 클래스에 컴파일 시의 타입 체크를 해주는 기능이다. 
컴파일을 할떄 사전에 타입을 체크 해줌으로써 코드의 안정성을 높일수 있다.

>장점
-   타입 안정성을 제공한다.
-   타입체크와 형변환을 생략할 수 있으므로 코드가 간결해진다.

>지네릭으로 클래스 선언

```java
package Generics;

public class GenericsEx1<T> {
	T item;
	
	void setItem(T item) {
		this.item = item;
	}
	T getItem() {
		return this.item;
	}
}
```

>주의사항
-   static에는 지네릭스를 적용할수 없다.
-   배열 new을 이용하여 주소를 할당 할때는 사용 할 수 없다.

>특정 클래스만 사용가능하게 적용하기.
```java
package Generics;

public class GenericsEx1<T extends Parent> {
	T item;
	
	void setItem(T item) {
		this.item = item;
	}
	T getItem() {
		return this.item;
	}
}
```

그외 제한 방법

~~~
<? extends T> 와일드의 상한 제한. T와 그 자손들만 사용 가능.
<? super T> 와일드의 하한 제한, T와 그 조상들만 사용 가능.  
<?> 제한없음
~~~
