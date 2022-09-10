---
title: C언어로 만든 큐 배열
author: kimjeahyun
date: 2022-08-15 01:00:00 +0900
categories: [자료구조]
tags: [자료구조]
---

# 큐란?

큐는 스택과 다르게 먼저 들어간 데이터가 먼저 나오는 방식이다.
해당 개념을 이용하여 C의 배열을 사용하여 큐 자료구조를 만들어보도록 하겠다.

>main.c

```c
#include <stdio.h>
#include <stdlib.h>
#include"Queue.h"

int main(void)
{

	Queue* queue = (Queue*)malloc(sizeof(Queue));
	InitQueue(queue);

	push(queue, 1);
	push(queue, 2);
	push(queue, 3);
	push(queue, 4);
	push(queue, 5);
	push(queue, 6);

	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));

	push(queue, 1);
	push(queue, 2);
	push(queue, 3);
	push(queue, 4);
	push(queue, 5);
	push(queue, 6);

	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));
	printf("%d \n", pop(queue));

	return 0;
}
```

>queue.c

```c
#include "Queue.h"

void InitQueue(Queue* queue) {
	queue->index = 0;
	queue->numOfQueue = 0;
	queue->cur = 0;
}
void push(Queue* queue, Data data) {
	
	if (queue->numOfQueue == Quene_Length) {
		printf("저장용량 초과");
		exit(1);
	}
	else {
		if (queue->index == Quene_Length) {
			queue->index = 0;
		}
		queue->queue[queue->index++] = data;
		queue->numOfQueue++;
	}
}
int pop(Queue* queue) {
	if (queue->numOfQueue == 0) {
		printf("값이 없음");
		exit(1);
	}
	if (queue->cur == Quene_Length) {
		queue->cur = 0;
	}
	queue->numOfQueue--;
	return queue->queue[queue->cur++];

}
int peek(Queue* queue) {
	return queue->queue[queue->cur];
}
```

>queue.h

```c
#ifndef __QUEUE_H__
#define __QUEUE_H__

#define TRUE 1
#define FALSE 0

#define Quene_Length 10

typedef int Data;

typedef struct _queue {
	Data queue[Quene_Length];
	int index;
	int numOfQueue;
	int cur;
}Queue;

void InitQueue(Queue* queue);
void push(Queue* queue, Data data);
int pop(Queue* queue);
int peek(Queue* queue);

#endif
```