---
title: C언어로 만든 List 단방향
author: kimjeahyun
date: 2022-08-06 20:00:00 +0900
categories: [DataStructure]
tags: [DataStructure]
---

# C언어를 통하여 자료구조 List 만들기

리스트 자료구조는 연결리스트 자료구조를 사용하였고
메모리를 할당해서 자료를 연결시킨다. 방향은 단방향이다.
거의 모든언어 에서 제공되는 List를 구현함으로써 얼마나 다른언어가 강력한지 다시 한번 깨닫게 되었다. C언어로 프로그램을 개발하게 된다면 소요시간이 매우 많이 걸릴것 같다.

기능은 다음과 같다.
-	추가
-	삭제
-	사이즈
-	가져오기

>List.h

```c
#ifndef __LIST_H_CUSTOM__
#define __LIST_H_CUSTOM__
#include<stdio.h>
#include<stdlib.h>

typedef enum { false, true } bool;

typedef struct _node {
	struct _node* next;
	int data;
	int index;
}Node;

typedef struct _list {
	Node* head;
	Node* tail;
	Node* cur;
	Node* prev;
	int size;
}List;

void initList(List* plist);
void add(List* plist, int data);
int length(List* plist);
int get(List* plist, int index);
bool remove(List* plist, int index);

#endif
```

>List.c

```c
#include "List.h"



void initList(List* plist) {
	plist->cur = NULL;
	plist->head = NULL;
	plist->tail = NULL;
	plist->size = 0;
}

void add(List* plist, int data) {
	
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;
	newNode->next = NULL;
	newNode->index = plist->size;

	if (plist->head == NULL) {
		plist->head = newNode;
	}
	else {
		plist->tail->next = newNode;
		plist->tail = newNode;
	}

	plist->tail = newNode;
	(plist->size)++;

}

int length(List* plist) {
	return plist->size;
}

int get(List* plist, int index) {
	if (index == 0) {
		return plist->head->data;
	}

	plist->cur = plist->head;

	while (plist->cur != NULL) {

		if (index == plist->cur->index) {
			return plist->cur->data;
		}
		plist->cur = plist->cur->next;
	}
	return 0;
}

bool remove(List* plist, int index) {
	
	bool isok = false;

	if (index == plist->head->index) {
		Node* newHead = (Node*)malloc(sizeof(Node));
		newHead = plist->head->next;
		free(plist->head);
		plist->head = newHead;
		plist->cur = newHead;
		isok = true;
	}
	else {
		plist->cur = plist->head->next;
		plist->prev = plist->head;

		while (plist->cur != NULL) {

			if (index == plist->cur->index) {
				plist->prev->next = plist->cur->next;
				free(plist->cur);
				plist->cur = plist->prev->next;
				isok = true;
				break;
			}
			plist->prev = plist->cur;
			plist->cur = plist->cur->next;
		}
	}
	(plist->size)--;

	if (isok == true) {
		while (plist->cur != NULL) {
			plist->cur->index = plist->cur->index - 1;
			plist->cur = plist->cur->next;
		}

	}
	return isok;
}
```

>main.c

테스트 함수 main


```c
#include <stdio.h>
#include <stdlib.h>
#include "List.h"



int main(void)
{
    List* list = (List*)malloc(sizeof(List));
    initList(list);
    add(list, 1);
    add(list, 2);
    add(list, 3);
    add(list, 4);
    add(list, 5);
    add(list, 6);
    add(list, 7);
    add(list, 8);
    add(list, 9);
    add(list, 10);


    printf("리스트의 사이즈: %d \n", length(list));

    for (int i = 0; i < list->size; i++) {
        printf("리스트 값: %d \n", get(list,i));
    }

    printf("\n\n");

    remove(list, 0);

    for (int i = 0; i < list->size; i++) {
        printf("인덱스: %d \n 리스트 값: %d \n", i, get(list, i));
    }

    printf("\n\n");

    remove(list, 1);

    printf("\n\n");

    for (int i = 0; i < list->size; i++) {
        printf("인덱스: %d \n 리스트 값: %d \n",i, get(list, i));
    }

    remove(list, 2);

    printf("\n\n");

    for (int i = 0; i < list->size; i++) {
        printf("인덱스: %d \n 리스트 값: %d \n", i, get(list, i));
    }

    remove(list, 6);

    printf("\n\n");

    for (int i = 0; i < list->size; i++) {
        printf("인덱스: %d \n 리스트 값: %d \n", i, get(list, i));
    }


    return 0;
}
```

> 출력값

~~~
리스트의 사이즈: 10
리스트 값: 1
리스트 값: 2
리스트 값: 3
리스트 값: 4
리스트 값: 5
리스트 값: 6
리스트 값: 7
리스트 값: 8
리스트 값: 9
리스트 값: 10

인덱스: 0
 리스트 값: 2
인덱스: 1
 리스트 값: 3
인덱스: 2
 리스트 값: 4
인덱스: 3
 리스트 값: 5
인덱스: 4
 리스트 값: 6
인덱스: 5
 리스트 값: 7
인덱스: 6
 리스트 값: 8
인덱스: 7
 리스트 값: 9
인덱스: 8
 리스트 값: 10

인덱스: 0
 리스트 값: 2
인덱스: 1
 리스트 값: 4
인덱스: 2
 리스트 값: 5
인덱스: 3
 리스트 값: 6
인덱스: 4
 리스트 값: 7
인덱스: 5
 리스트 값: 8
인덱스: 6
 리스트 값: 9
인덱스: 7
 리스트 값: 10

인덱스: 0
 리스트 값: 2
인덱스: 1
 리스트 값: 4
인덱스: 2
 리스트 값: 6
인덱스: 3
 리스트 값: 7
인덱스: 4
 리스트 값: 8
인덱스: 5
 리스트 값: 9
인덱스: 6
 리스트 값: 10

인덱스: 0
 리스트 값: 2
인덱스: 1
 리스트 값: 4
인덱스: 2
 리스트 값: 6
인덱스: 3
 리스트 값: 7
인덱스: 4
 리스트 값: 8
인덱스: 5
 리스트 값: 9

~~~

