---
title: 자바-쓰레드 2장 소개 
author: kimjeahyun
date: 2022-08-09 20:00:00 +0900
categories: [개발,자바,자바기초]
tags: [개발,자바,자바기초]
---

# 프로세스와 쓰레드

프로세스(process)란 메모리 자원이 할당되어 
프로그램이 실행중인것을 뜻한다.

구성
-   필요데이터
-   메모리
-   쓰레드

프로세스 구성도를 보멸 알수 있겠지만 무조건 1개이상의 
쓰레드를 가지고 있다. 쓰레드가 한개 일 때는 싱글쓰레드라 표현하며
두개 이상일 때는 멀티쓰레드라고 한다. 멀티쓰레드 프로세스 라고 한다.

>쓰레드의 개수는 제한이 있을까?
메모리에 의해 영향을 받으므로 메모리 한계에 따라 다르다.

# 멀티태스킹과 멀티쓰레딩

윈도우나 유닉스를 포함한 OS는 멀티태스킹을 지원한다.
멀티태스킹과 마찬가지로 멀티쓰레딩은 하나의 프로세스에서 
여러 쓰레드가 동시에 작업을 수행한다.


> 멀티쓰레딩의 장점
-   CPU의 사용률을 향상시킨다.
-   자원을 보다 효율적으로 사용 할 수 있다.
-   사용자에 대한 응답성이 향상된다.
-   작업이 분리되어 코드가 간결해진다.

걷기와 음악을 동시에드는 우리들
사람을 비유적으로 표현했을때 걷기와 음악을 듣는 행동도 멀티쓰레드라고 할수 있다. 만약 싱글쓰레드 일 경우 우리는 어떻게 될까?
걷기를 하고 있을때는 오직 걷기만 음악을 듣고있을때는 오직 음악만 듣고 다음 행동을 취할수 있다. 어려울 것이다.


# 싱글쓰레드와 멀티쓰레드의 구성
![쓰레드](../../img/java/thread.png)

다음 그림을 보면 알수 있지만 싱글쓰레드가 멀티쓰레드보다 더 효율적일 때가 있다 

- 싱글 코어일 경우 단순히 CPU만 사용하는 작업이라면 오히려 멀티쓰레드보다 싱글쓰레드가 효율적이다.

- 싱글쓰레드가 효율적인 이유는?
매순간 쓰레드가 실행될때는 쓰레드의 실행시간이 할당되는데 그 시간이 일정치 않다.

> 멀티쓰레드는 어디에 적합할까?

서로 다른 작업을 진행 시켜야 할때이다.


# 쓰레드의 우선순위

쓰레드는 우선순위라는 속성을 가지고 있는데
이 우선순위의 값에 따라 쓰레드가 얻는 실행시간이 달라진다. 쓰레드가 수행하는 작업의 중요도에 따라 쓰레드의 우선순위를 서로 다르게 지정하여 특정 쓰레드가 더 많은 작업시간을 갖도록 할 수 있다.

```java
    thread.setPriority(int); 
```

다음과 같이 setPriority 함수를 이용하여 우선순위를 지정할수 있다.

# 쓰레드의 그룹

쓰레드는 또한 그룹을 지어 클러스트 형태로 관리가 가능하다.
쓰레드는 또한 무조건 그룹이 포함되는데 앞서 생성한 쓰레드는 그룹을 지정하지 않으면 자동으로 자기가 속한 그룹으로 할당이 된다.


```java
package main;

public class GroupThread {
	
	public static void main(String[] args) {
		ThreadGroup main = Thread.currentThread().getThreadGroup();
		ThreadGroup group = new ThreadGroup("Group1");
		ThreadGroup SubGroup = new ThreadGroup(group,"SubGroup1");
		group.setMaxPriority(1);
		
		Runnable r = new Runnable() {

			@Override
			public void run() {
				// TODO Auto-generated method stub
				try {
					Thread.sleep(5000);
				} catch (InterruptedException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
			
		};
		
		new Thread(group,r,"th1").start();
		
		System.out.println(">> 쓰레드 그룹 목록 : "+main.getName() + 
						   ", 실행중인 그룹 쓰레드 개수: "+main.activeGroupCount()+
						   ", 실행중인 쓰레드 개수:"+main.activeCount());
		main.list();
	}

}

``` 

# 데몬 쓰레드

데몬 쓰레드는 다른 일반 쓰레드(데몬 쓰레드가 아닌 쓰레드)의 작업을 돋는 
보조적인 역할을 수행하는 쓰레드이다. 때문에 쓰레드가 모두 종료되면 데몬 쓰레드는 강제적으로 자동종료된다.

>데몬쓰레드 예제


```java
package main;

public class DaemonThread implements Runnable{

	static boolean autoON = true;
	
	public static void main(String[] args) {
		Thread thread = new Thread(new DaemonThread());
		
		thread.setDaemon(true);
		thread.start();
	
		for(int i = 1; i <= 10; i++) {
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			System.out.println(i);
			if(i == 5)
				autoON = false;
		}
	}
	
	@Override
	public void run() {
		// TODO Auto-generated method stub
		while(true) {
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			if(!autoON)
				autoSave();
			System.out.println("데몬 작동중");
		}
	}
	
	public void autoSave() {
		System.out.println("데몬 쓰레드 중지");
	}

}

```

