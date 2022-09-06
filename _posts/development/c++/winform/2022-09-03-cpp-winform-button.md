---
title: C++-winform 로그인화면 구현
author: kimjeahyun
date: 2022-09-03 11:30:00 +0900
categories: [개발,Cpp,Cpp기초]
tags: [개발,Cpp,Cpp기초]
---

# Winforms - login windows realizing

This is login windows composes one button and two textBox 
if you success login in then appearing MessageBox of success
if you failure login in then appearing MessageBox of failure

Let's go cording of winforms

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

