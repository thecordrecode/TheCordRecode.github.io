---
title: C++ - 구조체 및 포인터
author: kimjeahyun
date: 2022-08-26 20:00:00 +0900
categories: [개발,Cpp,Cpp기초]
tags: [개발,Cpp,Cpp기초]
---

# 구조체


구조체는 서로 관련된 연관이된 데이터를 한곳에 묶어서 저장하는 자료구조이다.

배열과 다른점은 다른 타입도 함께 저장 할 수 있다는 점이다.

# 구조체 생성

```cpp

//일회성 선언
struct{
	int variable1;
	string variable2;
}Structure

struct myStructType{
	int variable1;
	string variable2;
}

myStructType mt;

```

# 구조체 접근

```cpp

Structure.variable1 = 1;
Structure.variable2 = "txt";

mt.variable1 = 1;
mr.variable2 = "txt";

```


# 포인터

포인터는 주소값을 저장하는 변수이다.
따라서 주소값만 알고 있다면 어디서든지 해당 값을 접근할수 있다.

```cpp
#include<iostream>

using namespace std;


void changeNumber(int* number) {
	*number = 15;
}
void changeNumber(int number) {
	number = 15;
}
int main(void)
{
	int number = 10;
	int* ptrNumber = new int;
	*ptrNumber = 10;

	
	changeNumber(number);
	changeNumber(ptrNumber);
	cout << number << endl;
	cout << *ptrNumber << endl;

	return 0;
}
```