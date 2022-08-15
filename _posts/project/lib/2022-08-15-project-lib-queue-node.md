---
title: C언어로 만든 큐 노드
author: kimjeahyun
date: 2022-08-15 20:00:00 +0900
categories: [프로젝트,라이브러리]
tags: [프로젝트,라이브러리]
---

# 큐란?

큐는 스택과 다르게 먼저 들어간 데이터가 먼저 나오는 방식이다.
해당 개념을 이용하여 C의 배열을 사용하여 큐 자료구조를 만들어보도록 하겠다.

>main.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "queue.h"

int main(void) {

	Queue* queue = (Queue*)malloc(sizeof(Queue));

	InitQueue(queue);
	push(queue, 1);
	push(queue, 2);
	push(queue, 3);
	push(queue, 4);
	push(queue, 5);

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
#include <stdio.h>
#include <stdlib.h>
#include "queue.h"

void InitQueue(Queue* queue) {
	queue->head = NULL;
	queue->tail = NULL;
}
int isEmpty(Queue* queue) {
	if (queue->head == NULL) return TRUE;
	return FALSE;
}
Node* createNode(Data data) {
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;
	return newNode;
}
void push(Queue* queue, Data data) {
	Node* newNode = createNode(data);
	
	if (isEmpty(queue)) {
		queue->head = newNode;
		queue->tail = newNode;
	}	
	else {
		queue->tail->next = newNode;
		queue->tail = newNode;
	}
}
int pop(Queue* queue) {
	int data;

	if (queue->head == queue->tail)
	{
		data=queue->head->data;
		queue->head = NULL;
		queue->tail = NULL;
		return data;
	}
	if (isEmpty(queue)) return -987654321;

	data=queue->head->data;
	Node* removeNode = queue->head;
	queue->head = queue->head->next;
	free(removeNode);

	return data;
}
int peek(Queue* queue) {
	return queue->head->data;
}

```

>queue.h

```c
#ifndef __QUEUE_H__
#define __QUEUE_H__

#define TRUE 1
#define FALSE 0


typedef int Data;
typedef struct _node {
	struct _node* next;
	Data data;
}Node;

typedef struct _queue {
	Node* head;
	Node* tail;
}Queue;

void InitQueue(Queue* queue);
void push(Queue* queue, Data data);
int pop(Queue* queue);
int peek(Queue* queue);
int isEmpty(Queue* queue);
Node* createNode(Data data);
#endif
```