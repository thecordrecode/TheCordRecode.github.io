---
title: C++-template
author: kimjeahyun
date: 2022-09-03 11:30:00 +0900
categories: [개발,Cpp,Cpp기초]
tags: [개발,Cpp,Cpp기초]
---

# C++ template

Template는 C++에서 강력한 도구이다.


간단한 아이디어에서 시작되었는데 데이터 타입을 파라미터로 넘겨주는 개념이다.

이러한 개념으로 인하여 코드의 재 사용성을 증가시킨다.

​

Template 미 사용 

```cpp
#include <iostream>
#include <string>

using namespace std;

void print(int value) {
	cout << value << endl;
}
void print(char value) {
	cout << value << endl;
}
void print(string value) {
	cout << value << endl;
}

int main() {
	print(3);
	print("a");
	print("안녕하세요");
	return 0;
}
```

Template 사용

```cpp
#include <iostream>
#include <string>

using namespace std;

template<typename T> 
void print_v2(T value) {
	cout << value << endl;
}

int main() {
 
	print_v2(3);
	print_v2("a");
	print_v2("안녕하세요");

	return 0;
}
```

Template 사용해서 간단한 list 만들어보기.

```cpp
#include <iostream>
#include <string>

using namespace std;

template<typename T>
class cList {
public:
	struct Node {
		int index = 0;
		T value;
		Node* next = NULL;
	};
	Node* str = NULL;
	Node* end = NULL;
	void push_back(T value) {
		//처음 값이 들어간다. 
		if (str == NULL) {
			Node* tmp = new Node;
			tmp->index = 0;
			tmp->value = value;
			str = tmp;
			end = tmp;
		}
		else {
			Node* tmp = new Node;
			tmp->index = end->index + 1;
			tmp->value = value;

			Node* find = str;
			while (find->next != NULL) {
				find = find->next;
			}
			find->next = tmp;
			end = tmp;
		}
	}

	void show_list() {

		Node* iterator = str;
		do {
			cout << iterator->index << ":" << iterator->value << endl;
			iterator = iterator->next;
		} while (iterator->next != NULL);
		cout << iterator->index << ":" << iterator->value << endl;
	}

};

int main() {

	cList<string> cl;
	cl.push_back("일");
	cl.push_back("이");
	cl.push_back("삼");
	cl.push_back("사");
	cl.push_back("오");
	cl.show_list();

	cList<int> cl2;
	cl2.push_back(1);
	cl2.push_back(2);
	cl2.push_back(3);
	cl2.push_back(4);
	cl2.push_back(5);
	cl2.show_list();
	return 0;
}
```