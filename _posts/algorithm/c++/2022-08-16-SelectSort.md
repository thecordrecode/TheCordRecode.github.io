---
title: C++ 선택정렬
author: kimjeahyun
date: 2022-08-16 20:00:00 +0900
categories: [알고리즘]
tags: [알고리즘]
---


# 선택정렬

선택 정렬의 코드는 버블 정렬과 성능상 큰 차이가 없다.
다만 선택 정렬은 버블 정렬보다 더 쉽다. 모든 데이터를 한번씩 다 비교하여 
최솟값을 찾고 그 최소값과 비교시작점의 데이터를 맞바꿔 정렬을 진행한다.

그림으로 표현하면 다음과 같다.

인덱스 0 부터 최소값을 구한다.

![선택정렬](../../img/cpp/Algorithm/SelectSort1.png)

인덱스 1부터 최소값을 구한다.

![선택정렬2](../../img/cpp/Algorithm/SelectSort2.png)

인덱스 2부터 최소값을 구한다.

![선택정렬3](../../img/cpp/Algorithm/SelectSort3.png)

인덱스 3부터 최소값을 구한다.

![선택정렬4](../../img/cpp/Algorithm/SelectSort4.png)

자 다음 개념을 이용하여 선택 정렬을 구현해보도록 하겠다.


```cpp
#include <iostream>


int main(void) {


	int arrays[] = { 9,1,5,2,8,6,4,7,3 };
	int size = sizeof(arrays) / sizeof(int);
	//선택 정렬

	for (int i = 0; i < size; i++) {
		//가장 작은값을 구할거다.
		int minIndex = i;
		for (int j = i + 1; j < size; j++) {
			if (arrays[minIndex] > arrays[j]) {
				minIndex = j;
			}
		}
		int temp = arrays[i];
		arrays[i] = arrays[minIndex];
		arrays[minIndex] = temp;
	}

	//출력 구간
	for (int i = 0; i < size; i++) {
		std::cout << arrays[i] << std::endl;
	}

	return 0;
}
```

이상 선택 정렬 이었습니다.