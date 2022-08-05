---
title: 자바-예외처리
author: kimjeahyun
date: 2022-08-03 23:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 예외처리(Exception handling)

-   컴파일 에러 
    - 컴파일 시에 발생하는 에러
-   런타임 에러
    - 실행 시에 발생하는 에러
-   논리적 에러
    - 실행은 되지만, 의도와 다르게 동작하는 것 

자바에서 프로그램 실행시 에러 구분은 예외와 에러가 구분된다.

에러는 메모리 부족이나 스택오버플로우 와 같이 심각하여 복구할 수 없는 오류이고
예외는 발생하더라도 수습할수 있는 오류이다. 

에러 처리도 오브젝트와 마찬가지로 상위 최상위 오류가 존재한다. 
가장 최상위 오류 처리는 Exception 이다.

> 예외처리하기 -try-catch 문

```java
try{
    //수행할 문장
}catch(Exception1 e1){
    //예외1
}catch(Exception2 e2){
    //예외2
}catch(Exception3 e3){
    //예외3
}finally{
    //예외의 발생여부에 관계없이 항상 수행되어야 하는 문장
}
```

~~~
try 블럭 내에서 예외가 발생하는 경우
    발생한 예외와 일치하는 catch를 찾는다.
    일치하는 catch를 찾게 되면 catch 내용부분을 실행한다.
    만일 예외 처리 블럭을 찾지 못한다면 에러가 발생한다.
~~~

<br>

# throw 

throw 키워드를 통하여 프로그래머가 고의로 예외를 발생 시킬 수 있다.

```java
Exception exception = new Exception("예외를 던집니다.");
throw exception;
```

<br>

# 사용자정의 예외처리

```java
class MyException extends Exception{
    private fianl int ERR_CODE;

    MyException(String msg,int ERR_CODE){
        super(msg);
        this.ERR_CODE = ERR_CODE;
    }
    MyException(String msg){
        this(msg,100);
    }
    public int getErrCode(){
        return ERR_CODE;
    }
}
```