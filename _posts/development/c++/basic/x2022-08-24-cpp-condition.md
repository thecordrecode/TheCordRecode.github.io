---
title: C++-조건문
author: kimjeahyun
date: 2022-08-24 20:00:00 +0900
categories: [개발,Cpp,Cpp기초]
tags: [개발,Cpp,Cpp기초]
---


# 조건문

조건문은 조건을 통하여 TRUE or FALSE 에 대해 분기처리가 가능하다.

코딩을 하다보면 흐름을 바뀌는 형태가 많아지는데
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

```cpp
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

>main.cpp

```cpp
#include<iostream>
#include<string>

bool Login(std::string id, std::string passwd) {
	bool isok = false;


	if ("cordrecode" == id) {
		if ("good" == passwd) {
			isok = true;
			return isok;
		}
	}
	else {
		return isok;
	}

	return isok;

}

int main(void)
{

	if (Login("cordrecode", "good") == true) {
		std::cout << "로그인이 성공되었습니다.!" << std::endl;
	}
	
	return 0;
}

```

<br>

# switch 문

if문은 참과 거짓밖에 없기 때문에 경우의 수가 추가 될경우 else-if문을 계속해서 추가해야 한다. 그에 반해 switch 문은 하나의 조건문으로 여러개의 경우의 수를 처리 할 수 있다. 


```cpp
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

>main.cpp

```cpp

#include<iostream>
#include<string>

int Calc(int number, char oper, int number2) {

	switch (oper) {
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

int main(void)
{

	std::cout << Calc(10, '+', 5) << std::endl;
	std::cout << Calc(10, '/', 5) << std::endl;
	std::cout << Calc(10, '-', 5) << std::endl;
	std::cout << Calc(10, '*', 5) << std::endl;
	
	return 0;
}

```