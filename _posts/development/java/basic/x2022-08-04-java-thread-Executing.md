---
title: 자바-쓰레드의 소개
author: kimjeahyun
date: 2022-08-03 23:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 쓰레드의 구현과 실행

쓰레드를 구현하는 방법은 Thread클래스를 상속받는 방법관 Runnable 인터페이스를 구현하는 방법 모두 두 가지가 있다. 어느 쪽을 선택하든 별차이는 없지만 상속을 받아 구현을 한다면 다른 클래스를 상속받을수 없기 때문에 인터페이스를 사용해서 구현하는것이 좋다.

>Thread 클래스를 상속

```java

class MyThead extends Thread{
    public void run(){
        //작업 내용
    }
}

```

>Runnable 인터페이스를 구현

```java
class MyThread implements Runnable{
    public void run(){
        //작업 내용
    }
}
```

Runnable 인터페이스는 오로지 Run()만 정의되어 있는 간단한 예제이다.


>쓰레드를 이용한 구현 코드

```java

class ThreadEx1{
    public static void main(String args[]){
        ThreadEx1_1 t1 = new ThreadEx1_1();
        Runnable r = new ThreadEx1_2();
        Thread t2 = new Thread(r);
        t1.start();
        t2.start();
    }

    class ThreadEx1_1 extends Thread{
        public void run(){
            //
        }
    }

    class ThreadEx1_2 implements Runnable{
        public void run(){
            //
        }
    }
}

```

Runnable 인터페이스를 구현한 경우 Runnable인터페이스를 구현한 클래스의 인스턴스를 생성한 다음 , 이 인스턴스를 Thread클래스의 생성자의 매개변수로 제공해야 한다.

