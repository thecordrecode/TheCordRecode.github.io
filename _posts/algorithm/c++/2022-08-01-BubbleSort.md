---
title: C++ 버블정렬
author: kimjeahyun
date: 2022-08-16 01:00:00 +0900
categories: [알고리즘]
tags: [알고리즘]
---


# 버블정렬

버블 정렬은 정렬의 알고리즘중 가장 기본이 되고 많이 알려진 알고리즘이다.
또한 구현 난이도가 가장 쉽다. 버블 정렬은 두 개의 데이터를 비교해가면서 정렬을 진행하는 방식이다. 

정렬의 진행방식은 

다음과 같이 배열이 주어질때. 9,1,5,2 정렬 방식은 다음과 같다.

9와 1을 비교 9가 크다면 서로의 데이터 위치변경

1,9,5,2

9와 5을 비교 9가 크다면 서로의 데이터 위치변경

1,5,9,2

9와 2을 비교 9가 크다면 서로의 데이터 위치변경

1,5,2,9

제일 큰 수를 맨 마지막으로 보넀으니 맨 마지막 수를 제외하고 똑같은 방법으로 
정렬을 다시 시작

1와 5을 비교 1가 크다면 서로의 데이터 위치변경

1,5,2,9

5와 2을 비교 5가 크다면 서로의 데이터 위치변경

1,2,5,9

정렬 완성!

자 다음 개념을 이용하여 버블정렬을 구현해보도록 하겠다.

```cpp
#include <iostream>



int main(void) {

	int arrays[] = { 9,1,5,2,8,6,4,7,3 };

	int size = sizeof(arrays) / sizeof(int);

	//버블 정렬

	for (int i = 0; i < size; i++) {

		for (int j = 0; j < size - i-1; j++) {

			if (arrays[j] > arrays[j + 1]) {
				int temp = arrays[j];
				arrays[j] = arrays[j + 1];
				arrays[j + 1] = temp;
			}

		}

	}

	//출력 구간
	for (int i = 0; i < size; i++) {
		std::cout << arrays[i] << std::endl;
	}

	return 0;
}
```

이상 버블 정렬 이었습니다.