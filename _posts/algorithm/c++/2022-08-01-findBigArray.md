---
title: C++ 배열에서 가장 많이 등장하는 수는?
author: kimjeahyun
date: 2022-08-01 12:00:00 +0900
categories: [Algorithm]
tags: [Algorithm]
---


# C++ 배열에서 가장 많이 등장하는 수는?

> [1,1,5,5,2,3,5,5] 중 가장 많이 등장 하는 수는 5이다. 

해당 부분을 구하는 로직을 for문을 이용하여 구현 하도록 하겠습니다.

> 2중 for문 일때.

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

> 1중 for문 일때.

```java
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


> 속도 테스트


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

속도 테스트를 해보시면 알겠지만 
매우 큰 차이가 발생하는 것을 알수 있다. 배열의 크기가 커질수록 속도 차이는 매우 급격하게 차이가 난다. 

