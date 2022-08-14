---
title: C언어로 만든 stack 노드
author: kimjeahyun
date: 2022-08-14 12:00:00 +0900
categories: [프로젝트,라이브러리]
tags: [프로젝트,라이브러리]
---

# 스택이란?

스택은 컴퓨터에서 사용되는 기본 데이터 구조중 하나이며 후입선출이다.
다음 자료구조를 C언어 배열을 통하여 구현해 보았다.


>main.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "stack.h"


int main(void) {

	Stack* stack = (Stack*)malloc(sizeof(Stack));

	InitStack(stack);
	push(stack, 1);
	push(stack, 2);
	push(stack, 3);
	push(stack, 4);
	push(stack, 5);
	push(stack, 6);
	push(stack, 7);
	push(stack, 8);
	push(stack, 9);

	printf(" %d\n ", peek(stack));

	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));
	printf("%d\n ", pop(stack));

	return 0;
}
```

>stack.c

```c
#include "stack.h"
#include<stdlib.h>

void InitStack(Stack* stack) {
	stack->head = (Node*)malloc(sizeof(Node));
	stack->numOfNode = 0;
}
void push(Stack* stack, Data data) {
	
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;
	if (stack->head->next == NULL) {
		stack->head->next = newNode;
	}
	else {
		newNode->next = stack->head->next;
		stack->head->next = newNode;
	}
	stack->numOfNode++;
}
int pop(Stack* stack) {
	int data = 0;
	Node* removeNode;
	if (stack->numOfNode == 0) return;
	if (stack->numOfNode == 1) {
		data = stack->head->next->data;
		free(stack->head->next);
	}
	else {
		data = stack->head->next->data;
		removeNode = stack->head->next;
		stack->head->next = stack->head->next->next;
		free(removeNode);

	}
	stack->numOfNode--;
	return data;
}
int peek(Stack* stack) {
	return stack->head->next->data;
}
```

>stack.h

```c
#ifndef __STACK_H__
#define __STACK_H__

#define TRUE 1
#define FALSE 0

typedef int Data;

typedef struct __node{
	struct __node* next;
	Data data;
}Node;

typedef struct __stack {
	Node* head;
	int numOfNode;
}Stack;


void InitStack(Stack* stack);
void push(Stack* stack, Data data);
int pop(Stack* stack);
int peek(Stack* stack);

#endif
```