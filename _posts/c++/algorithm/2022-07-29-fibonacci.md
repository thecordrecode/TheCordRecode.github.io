---
title: C++ 피보나치 수열구하기
author: kimjeahyun
date: 2022-07-28 17:00:00 -0500
categories: [C++언어,알고리즘]
tags: [C++언어,알고리즘]
---


# C++ 피보나치 구하기

피보나치는 1 , 1 , 2, 3 , 5 , 8 , 13 , 21 .... 으로 이루어지는 수 입니다.

규칙을 간단히 설명하자면 다음 피보나치를 구하는 방법은
이전의 피보나치 수와 현재의 피보다 치수를 더하면 다음의 피보나치 수를 구할 수 있다.

재귀 함수와 for 문 함수를 각각 이용하여 피보나치를 구하는 방법 두 가지를 소개하겠습니다.

for문을 이용하여 구현한 피보나치

```cpp
int Fibonacci= 0, prevFibonacci = 0, pprevFibonacci = 1;

	for (int i = 0; i < 30; i++) {
		cout << Fibonacci << endl;
		Fibonacci = prevFibonacci + pprevFibonacci;
		pprevFibonacci= prevFibonacci ;
		prevFibonacci = Fibonacci ;
```

재귀 함수를 이용하여 구현한 피보나치

```cpp
void Fibonacci(int prevFibonacci,int pprevFibonacci) {
	if (prevFibonacci > 10000) return;
	cout << prevFibonacci + pprevFibonacci << endl;
	Fibonacci(prevFibonacci + pprevFibonacci, prevFibonacci);
}
```

이상 C++를 이용하여 피보나치를 구하는 로직이였습니다.
