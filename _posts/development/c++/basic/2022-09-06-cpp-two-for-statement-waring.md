---
title: C++-2중 for문
author: kimjeahyun
date: 2022-09-06 00:00:00 +0900
categories: [Languages for development,Cpp]
tags: [Languages for development,Cpp]
---

# C++ 2중 for문

C++에서 주어진 배열 중 가장 많이 등장하는 숫자를 구하는 함수를 생성


2중 for 문 버전 

```cpp
int majority1(const vector<int>& A) {
	int N = A.size();
	int majority = -1, majorityCount = 0;

	for (int i = 0; i < N; ++i) {
		int V = A[i], count = 0;

		for (int j = 0; j < N; ++j) {
			if (A[j] == V) {
				++count;
			}
		}

		if (count > majorityCount) {
			majorityCount = count;
			majority = V;
		}
	}
	return majority;
}
```

1중 for 문 버전

```cpp
int majority2(const vector<int>& A) {
	int N = A.size();
	int max = 0;
	int majority = 0;

	vector<int> vect(N, 0);

	for (int i = 0; i < N; i++) {
		++vect[A[i]];
		if (max < vect[A[i]]) {
			max = vect[A[i]];
			majority = A[i];
		}
	}
	return majority;
}
```

테스트

```cpp
int main() {

	vector<int> vc;

	for (int i = 0; i < 70000; i++) {
		vc.push_back(rand() % 100);
	}
	clock_t start, end;
	double result;

	start = clock();
	cout << majority2(vc) << endl;
	end = clock();
	result = (double)(end - start);
	cout << result << endl;

	start = clock();
	cout << majority1(vc) << endl;
	end = clock();
	result = (double)(end - start);
	cout << result << endl;
	

	return 0;
}
```

테스트 결과 

버전2 1중 for 문 0.001초 소요

버전1 2중 for 문 12.360 초 소요

