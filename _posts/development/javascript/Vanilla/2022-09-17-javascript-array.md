---
title: 자바스크립트 - array
author: kimjeahyun
date: 2022-09-17 00:00:00 +0900
categories: [Languages for development,JavaScript]
tags: [Languages for development,JavaScript]
---

# javaScript Array

Array란? 하나 이상의 값을 저장 할 수 있는 자료 구조이다.
배열을 사용 하는 이뉴는? 만약에 값을 3개를 사용하고 싶다하면 3번 선언해야 한다.
값을 변경 할 때도 변수이름을 하나 하나씩 찾아서 고치기란 쉽지 않다.


```javascript
const arrays = ["value1","value2","value3"];
```

배열의 메소드 

# 배열을 문자열로 변경해주는 toString

```javascript
const arrays = ["value1","value2","value3"];
console.log(arrays.toString());
```

# toString 과 비슷한 join 
> 차이점! toString은 , 로 정해져 있지만 join은 값을 정 할 수 있다.

```javascript
const arrays = ["value1","value2","value3"];
console.log(arrays.join(" * "));
```

# 배열의 값을 꺼낼 수 있는 pop 
> 마지막 값을 제거하고 그 값을 반환 시킨다.

```javascript
const arrays = ["value1","value2","value3"];
console.log(arrays.pop());
console.log(arrays);
```

# 배열의 값을 꺼낼 수 있는 shift
> 앞에서 값을 제거하고 그 값을 반환 시킨다.

```javascript
const arrays = ["value1","value2","value3"];
console.log(arrays.shift());
console.log(arrays);
```

# 배열의 값을 추가 할 수 있는 push

```javascript
const arrays = ["value1","value2","value3"];
arrays.push("value4");
console.log(arrays);
```

# 배열의 값을 추가 할 수 있는 unshift

```javascript
const arrays = ["value1","value2","value3"];
arrays.unshift("value0");
console.log(arrays);
```

# 배열의 길이를 구하는 length

```javascript
const arrays = ["value1","value2","value3"];
console.log(arrays.length);
```

# 배열을 합칠 수 있는 concat

```javascript
const arrays = ["value1","value2","value3"];
const arrays2 = ["value1","value2","value3"];
console.log(arrays.concat(arrays2));
```

