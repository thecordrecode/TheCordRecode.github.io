---
title: 자바-오버로딩
author: kimjeahyun
date: 2022-08-02 20:00:00 +0900
categories: [Languages for development,Java]
tags: [Languages for development,Java]
---

# 오버로딩(overloading)

오버로딩 이란? 
우리가 함수를 작성할때 Method 라는 함수가 존재할때.
같은 이름을 중복하여 작성하는 것이다. 단 같은 이름이라 하더라도 매겨변수 및 반환 타입이 다를떄만 작성이 가능하다.

정리하면 다음과 같다.
-	함수의 이름이 같아야 한다.
-	매겨변수 및 타입이 중복되면 안된다.


클래스,함수,오버로딩을 이용하여 
console.log 라는 함수를 정의하도록 하겠다. 

```java
package conditionWhile;

public class console {
	
	void log(String value) {
		System.out.println(value);
	}
	void log(int value) {
		System.out.println(value);
	}
	void log(double value) {
		System.out.println(value);
	}
}
```

> 다음과 같이 log라는 함수가 여러번 정의가 된것을 볼 수 있는데 이것이 바로 오버로딩이다. 여기서 가장 큰 장점은
이름을 따로 구분하지 않고 하나의 이름을 통하여 정의 할 수 있다는 것이다.
만약 오버로딩이 지원되지 않을경우 logString logInt logDouble 이라는 함수형태가 생성되야 할 거이다. 이것은 매우 비효율적이다.

<br>

# 가변인자

```java
public void log(String... value) {
		for(String item:value) {
			System.out.println(item);
		}
	}
```

가변인자란 매개변수가 여러개 일 경우 자동으로 할당해준다. 다음과 같이 매개변수가 몇개 올지 모르는 경우 가변인자를 통하여 해결 가능하다.
