---
title: C++ 퀵정렬
author: kimjeahyun
date: 2022-08-22 17:00:00 +0900
categories: [알고리즘]
tags: [알고리즘]
---


# 퀵정렬

퀵정렬의 개념은 피봇 기준점을 정하고 배열을 맨 왼쪽 과 오른쪽을 구한다음
기준점을 기준으로 왼쪽에 대한 값을 클때까지 위치를 증가시키고
오른쪽에 대한 값을 작을때 까지 값을 위치를 감소 시킨다. 

위치를 다 변경후 왼쪽 값과 오른쪽에 해당하는 값을 변경시킨다.
차후 왼쪽 값의 위치와 오른쪽값의 위치가 변경되었을때 까지 다음 작업을 반복한후 반복문 종료후 피봇점과 오른쪽 값 위치 값을 변경한다. 
그런 다음 피봇값의 위치를 반환시켜 재귀를 이용하여 정렬을 진행시킨다.


자 다음 개념을 이용하여 병합 정렬을 구현해보도록 하겠다.



```cpp
#include<iostream>

void swapArrayData(int arr[], int idx1, int idx2){
	int temp = arr[idx1];
	arr[idx1] = arr[idx2];
	arr[idx2] = temp;
}

int Partition(int arr[], int left, int right) {

	int pivot = arr[left];
	int low = left+1;
	int high = right;

	while (low <= high) {

		while (pivot > arr[low]) {
			low++;
		}
		while (pivot < arr[high]) {
			high--;
		}
		if (low <= high) {
			swapArrayData(arr, low, high);
		}
	}
	swapArrayData(arr, left, high);
	return high;

}

void QuickSort(int arr[], int left, int right) {

	if (left <= right) {

		int pivot = Partition(arr, left, right);
		QuickSort(arr, left, pivot - 1);
		QuickSort(arr, pivot + 1, right);

	}

}

int main(void) {

	int arr[10] = { 9,10,5,1,8,4,7,6,2,3 };

	int length = sizeof(arr) / sizeof(int);
	int i;

	QuickSort(arr, 0, length - 1);

	for (i = 0; i < length; i++) {
		std::cout << arr[i] << std::endl;
	}

	return 0;
}
```

이상 퀵 정렬 이었습니다.