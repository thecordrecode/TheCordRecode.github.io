---
title: 자바-쓰레드 1장 소개 
author: kimjeahyun
date: 2022-08-08 23:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 쓰레드의 구현과 실행

쓰레드를 사용하는 방법에 대해서는 두가지가 존재하는데

-   Thread 클래스를 상속받는법
-   Runnable 인터페이스를 구현하는 방법

다만 클래스로 상속 받을경우 다른 클래스를 상속 받을수 없다는 단점이 있다.

>Thread 클래스를 상속

```java

class FirstThead extends Thread{
    public void run(){
        //작업 내용
    }
}

```

>Runnable 인터페이스를 구현

```java
class FirstThead implements Runnable{
    public void run(){
        //작업 내용
    }
}
```

Runnable 인터페이스는 오로지 Run()만 정의되어 있는 간단한 예제이다.


>쓰레드를 이용한 구현 코드

```java

class ThreadExam{
    public static void main(String args[]){
        ThreadExam_1 t1 = new ThreadExam_1();
        Runnable r = new ThreadExam_2();
        Thread t2 = new Thread(r);
        t1.start();
        t2.start();
    }

    class ThreadExam_1 extends Thread{
        public void run(){
            //
        }
    }

    class ThreadExam_2 implements Runnable{
        public void run(){
            //
        }
    }
}

```

Runnable 인터페이스를 구현한 경우 Runnable인터페이스를 구현한 클래스의 인스턴스를 생성한 다음 , 이 인스턴스를 Thread클래스의 생성자의 매개변수로 제공해야 한다.

지금까지 간단한 쓰레드 사용방안에 대해 알아보았다.