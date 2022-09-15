---
title: 자바스크립트 - string
author: kimjeahyun
date: 2022-09-16 00:00:00 +0900
categories: [개발,자바스크립트]
tags: [개발,자바스크립트]
---

# 자바스크립트 String


String 이란 값을 저장하고 문자를 조작하기 위해 생겨나게된 자료형이다.
String 내부에는 빈값을 저장하거나 여러 줄의 문자를 저장 할 수 있다.


> Example 1

```javascript
//double quotes
let name = "김재현";

//single quotes
let name = '김재현';
```

> String 함수 모음집

글자의 문자 길이 구하기

```javascript

let name = '김재현';
let nameLength = name.length;

```

문자를 추출 하는 방법

# slice

```javascript
let name = '김재현';
let firstName = name.slice(0,1);
```

# substring

```javascript
let name = '김재현';
let firstName = name.substring(0,1);
```

# substr

```javascript
let name = '김재현';
let secondName = name.substr(1,2);
```

# 문자열 문자 변경하기

```javascript
let name = '김재현';
let replacedName = name.replace("김","");
```

# 문자를 대문자 및 소문자로 변경하기


```javascript
let text = "hello world!!";
let upperText = text.toUpperCase();
let lowerText = upperText.toLowerCase();
```


# 문자열 합치기

```javascript
let text1 = "Hello";
let text2 = "world";
let text3 = text1.concat(" ",text2);
```

# 문자열 빈공간 지우기

```javascript
let text1 = "       Hello World!            ";
let text2 = text1.trim();
let text3 = text1.trimStart();
let text4 = text1.trimEnd();
```

# padStart

```javascript
let text = "010-";
text = text.padEnd(8,"x");
text = text + "-";
text = text.padEnd(13,"x");
```

# 문자열 나누기

```javascript
let text = "heloworld!";
let array = text.split("");
```

# 문자열 찾기 문자열이 없으면 -1

```javascript
let str = "Hello world!";
let findstr = str.indexOf("Hello");
```

# 문자열 찾기 Search

```javascript
let str = "Hello world!";
let findstr = str.search("Hello");
```

# 문자열 찾기 includes

```javascript
let str = "Hello world!";
let findstr = str.includes("Hello");
``