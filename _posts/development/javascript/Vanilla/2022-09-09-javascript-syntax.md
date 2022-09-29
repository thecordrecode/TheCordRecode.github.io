---
title: 자바스크립트 - 문법
author: kimjeahyun
date: 2022-09-09 15:00:00 +0900
categories: [Languages for development,JavaScript]
tags: [Languages for development,JavaScript]
---

이장은 자바스크립트에 문법은 짧은 시간내에 상기 시킬정도의 정리만 하였다.

# 자바스크립트 문법

자바스크립트에서 값을 정의할 때 두 가지 종류가 있다.

-   상수
-   변수

상수란? 
값이 변하지 않은 값을 의미한다 예를 들어 3.14 파이라든가 시리얼번호 등이 이에 해당된다.

변수란?
변수란 값이 변하는 값을 의미한다.

# 주석처리하기

주석이란 프로그램에서 무시되며 코드로 실행되지 않는 것을 말한다.

자바스크립트 프로그래밍 내부에서 주석처리하는 방법

1줄만 주석처리하는 방법

// 를 사용하여 단일주석 처리를 할 수 있다.

```javascript
//주석처리 입니다.
```

여러줄 주석처리하는 방법

/**/ 를 사용하여 다중주석 처리를 할 수 있다.

```javascript
/*
주석처리 입니다.
주석처리 입니다.
주석처리 입니다.
*/
```

# 변수 선언하기

변수란 값을 담는 바구니라고 생각하면 된다.

자바스크립트에서 변수를 선언하는 방법은 그렇게 어렵지 않다.
3가지의 키워드만 알고 있으면 된다.

-   let
-   var
-   const
    -   상수값을 저장할때 사용된다.

또한 변수를 선언할 때 대소문자 구분한다는 것을 알아두자.

여기서 타 언어와 다른점은 변수를 선언할때 타입을 선언하지 않는다는 것이다.
데이터 타입은 프로그래멍 언어에서 매우 중요한 개념인데. 자바스크립트는 변수 값을 넣거나 선언할때 자동적으로 타입이 변경된다.


```javascript
// Let으로 변수 선언하기

let name = "김재현";

// var로 변수 선언하기

var name = "김재현";

// const로 변수 선언하기

const name = "김재현";

```

여기서 궁금한점 그렇다면 
let과 var의 차이점은 무엇일까?

let은 재정의가 불가능 하다.
다음과 같은 구문이 있을 경우 let를 재선언 할 수 없다.

```javascript
let cannotdeclare = "value";

let cannotdeclare = "would This be declared in the code?";
```

```javascript
var candeclare = "value";

var candeclare = "would This be declared in the code?";
```

let은 블럭구조 내부에서만 사용될수 있다.

```javascript

{
    let value = "good";
}

// value can Not be used here

{
    var value = "good";
}

// value can be used here


```

# 자바스크립트 Operators

자바스크립트에서 타언어에서 제공하는 Operators를 제공한다.
다만 자바스크립트에서 특이한점은 문자도 operators를 사용할수 있다는 것이다.
Operators 다른 언어와 비슷하니 아래에서 공부

[https://thecordrecode.github.io/posts/java-operator](https://thecordrecode.github.io/posts/java-operator)


# 자바스크립트 함수

자바에서 함수를 선언할때는 function 키워드를 사용하여 정의된다.

```javascript


//리턴값이 없는 함수
function name(parameter1,parameter2,........){
    //code to be executed
}

//리턴값이 있는 함수
//여기서 중요한점은 자바스크립트는 함수에 리턴 타입을 안적는 다는 것이다.
function name(paramter1,parameter2,...){

    return null;
}


```

# 자신이 호출하는 함수 선언하기

```javascript

(function(){
    alert("Hello world");
})();

```

# Arrow function 

function 키워드를 이용한 함수 선언뿐만 아니라 Arrow 함수를 이용하여 함수를 선언 할 수 있다.

```javascript

const func = () => {

};

const func = (parameter1,parameter2) => {

};

const func = (parameter1,parameter2) => {
    return value;
};
```


# 자바스크립트 객체

자바스크립트에서도 C++의 구조체와 같이 객체를 선언 할 수 있다.


>사람 객체 만들기


```javascript

const person = {
    name: "김재현",
    age:28
}

```

사람객체 속성값 접근하기.

```javascript

person.name;
person.age;

person["name"];
person["age"];

```

> 객체 안에서는 함수를 선언 할 수 있다.

```javascript
const person = {
    name: "김재현",
    age:28,
    introduce: function(){
        return this.name + " " + this.age; 
    }
}
```

> 여기서 This는 무엇일까?


자바스크립트에서 This 키워드는 객체를 참조한다.
this가 어디에서 호출하냐에 따라서 객체에 대한 참조 방향성이 달라진다.

-   객체 함수 내부에서는 Object를 기준으로 한다.
-   평구문에서 사용할 경우 글로벌 오브젝트를 참조한다.
-   함수 내에서 사용할 경우 글로벌 오브젝트를 참조한다.
-   strict mode 에서 함수 내에서 사용 할 경우 undefined 상태이다.
-   이벤트에서 사용할 경우 element 를 참조한다.
-   call() , apply() , bind() 어느 객체든 참조할수 있다.


# 자바스크립트 조건문 배우기

조건문 문법

```javascript

//조건문 1
if (condition){
    // 조건부가 true일 경우 다음 구문이 실행된다.
}

//조건문 2
if (condition){

}
else{

}

//조건문 3

if (condition){

}
else if(condition){

}
else{

}

```

> switch 구문을 이용하여 조건문을 구현 할 수 있다.

```javascript
switch(expression){
    case x:
        //code block
        break;
    case y:
        //code block
        break;
    default:
        //code block
}
```

> break 키워드

break 키워드가 실행 되었을때는 코드가 중단된다.

> default 키워드

default 키워드는 조건에 도달하지 못하였을때 무조건 실행 되는 코드이다.


# 자바스크립트 반복문 배우기

For 반복문 문법

```javascript

for(var i = 0; i < 10; i++){
    //code block to be executed
}

```

For in Loop
객체 배열이 있을때 다음과 같이 반복문 사용 가능

```javascript

for(key in arrays){
    //code block to be executed
}


arrays.forEach(()=>{
    //code block to be executed
})

```

while문을 통한 반복문

```javascript

while(조건부)
{
    //code block to be executed
}

do
{
    //code block to be executed
}
while(조건부)

```


# 자바스크립트 클래스

기본 선언 방법

```javascript

class ClassName{
    constructor(){
        //생성자
    }
    method_1(){
        //..
    }
}

```

상속 받기

```javascript

class ClassName extends parentClassName{
    //super -> parent Class
    //this -> current Class
}

```