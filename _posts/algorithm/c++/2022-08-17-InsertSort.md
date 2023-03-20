---
title: C++ 삽입정렬
author: kimjeahyun
date: 2022-08-17 20:00:00 +0900
categories: [Algorithm]
tags: [Algorithm]
---


# 삽입정렬

정렬이 안되어 있는 부분에 있는 데이터를 정렬 된 부분의 특정 위치에 삽입해 가는 알고리즘이다. 



그림으로 표현하면 다음과 같다.

![삽입정렬](../../img/cpp/Algorithm/insertSort.png)

자 다음 개념을 이용하여 삽입 정렬을 구현해보도록 하겠다.



```cpp
#include <iostream>

int main(void)
{

	int arr[] = { 8,9,5,4,6,10,1,7,3,2 };
	int size = sizeof(arr) / sizeof(int);

	int data = 0;
	for (int i = 1; i < size; i++)
	{
		data = arr[i];
		for (int j = i - 1; j >= 0; j--) {
			if (data < arr[j]) {
				arr[j + 1] = arr[j];
			}
			else {
				break;
			}
			arr[j] = data;
		}
	}

	for (int i = 0; i < size; i++) {
		std::cout << arr[i] << std::endl;
	}

	//4,5,1,3,2
	//4 1 5 3 2

	return 0;
}
```

이상 삽입 정렬 이었습니다.