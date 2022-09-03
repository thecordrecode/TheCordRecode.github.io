---
title: C++-namespace
author: kimjeahyun
date: 2022-09-03 11:30:00 +0900
categories: [개발,Cpp,Cpp기초]
tags: [개발,Cpp,Cpp기초]
---

# namespace

네임스페이스란 코드의 지역을 나누어주는 역활이라고 생각하면 된다. 예를 들어
print 라는 함수가 있을때. 같은 명칭에 다른 기능을 정의하고 싶을때 사용된다는 것이다.

> 예제

```cpp
#include <iostream>



namespace person {
	void print(std::string value) {
		std::cout << "Person Function" << std::endl;
		std::cout << value << std::endl;
	}
}

namespace product {
	void print(std::string value) {
		std::cout << "product Function" << std::endl;
		std::cout << value << std::endl;
	}
}

int main() {


	person::print("TEST");
	product::print("TEST");

	return 0;
}
```

다음 예제에서 print 라는 함수를 네임 스페이스를 이용하여 정의 한것이다. 만약 네임스페이스를 사용하지 않는다면? 각각의 맞춰 함수 네이밍을 변경해주어야 한다. 

> 예제

```cpp
#include <iostream>

void print_person(std::string value) {
	std::cout << "Person Function" << std::endl;
	std::cout << value << std::endl;
}
void print_product(std::string value) {
	std::cout << "product Function" << std::endl;
	std::cout << value << std::endl;
}

int main() {


	print_person("TEST");
	print_product("TEST");

	return 0;
}
```


또한 네임스페이스는 중복으로 정의 할수 있다.

```cpp
#include <iostream>



namespace person {
	namespace function {
		void print(std::string value) {
			std::cout << "Person Function" << std::endl;
			std::cout << value << std::endl;
		}
	}
}


int main() {

	person::function::print("Good");

	return 0;
}
```

using namespace를 이용하여 네임스페이스를 생략할수도 있다.


```cpp
#include <iostream>



namespace person {
	namespace function {
		void print(std::string value) {
			std::cout << "Person Function" << std::endl;
			std::cout << value << std::endl;
		}
	}
}


int main() {

	using namespace person::function;
	print("Good");

	return 0;
}
```