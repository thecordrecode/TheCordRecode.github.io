---
title: C언어로 만든 stack 배열
author: kimjeahyun
date: 2022-08-13 20:00:00 +0900
categories: [DataStructure]
tags: [DataStructure]
---

# 스택이란?

스택은 컴퓨터에서 사용되는 기본 데이터 구조중 하나이며 후입선출이다.
다음 자료구조를 C언어 배열을 통하여 구현해 보았다.


>main.c

```c
#include<stdio.h>
#include"ArrayBaseStack.h"

int main(void) {

	Stack stack;
	StackInit(&stack);

	SPush(&stack, 1);
	SPush(&stack, 2);
	SPush(&stack, 3);
	SPush(&stack, 4);
	SPush(&stack, 5);

	while (!SIsEmpty(&stack))
		printf("%d ", SPop(&stack));

	return 0;
}
```

>stack.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "ArrayBaseStack.h"

void StackInit(Stack* pstack)
{
	pstack->topIndex = -1;
}

int SIsEmpty(Stack* pstack) {
	if (pstack->topIndex == -1)
		return TRUE;
	else
		return FALSE;
}

void SPush(Stack* pstack, Data data) {
	pstack->topIndex += 1;
	pstack->stackArr[pstack->topIndex] = data;
}

Data SPop(Stack* pstack) {
	int index;

	if (SIsEmpty(pstack)) {
		printf("Stack Memory Error!");
		exit(-1);
	}

	index = pstack->topIndex;
	pstack->topIndex -= 1;
	return pstack->stackArr[index];
}

Data SPeek(Stack* pstack) {
	if (SIsEmpty(pstack)) {
		printf("Stack Memory Error!");
		exit(-1);
	}

	return pstack->stackArr[pstack->topIndex];
}

```

>stack.h

```c
#ifndef __AB_STACK_H__
#define __AB_STACK_H__

#define TRUE 1
#define FALSE 0
#define STACK_LEN 100

typedef int Data;

typedef struct _arrayStack 
{
	Data stackArr[STACK_LEN];
	int topIndex;
}ArrayStack;

typedef ArrayStack Stack;

void StackInit(Stack* psTack);
int SIsEmpty(Stack* psTack);

void SPush(Stack* pstack, Data data);
Data SPop(Stack* pstack);
Data SPeek(Stack* pstack);


#endif 
```