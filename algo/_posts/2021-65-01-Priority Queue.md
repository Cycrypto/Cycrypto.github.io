---
layout: grid
title: Example Content
description: >
	우선순위 큐에 대해 알아본다
sitemap: false
hide_last_modified: true
---

# 우선순위 큐

## 정의

* 우선순위를 가진 항목들을 저장하는 큐

* FIFO 가 아닌 우선순위가 높은 데이터가 먼저 나감.

  > 시뮬레이션 시스템
  >
  > 네트워크 트레픽 제어
  >
  > 운영체제의 작업 스케줄링



## ADT

> * create() : 우선순위 큐를 생성함
> * init(q) : 우선순위 큐 q를 초기화 함
> * is_empty(q) : 우선순위큐 q가 비었는지 검사함
> * is_full(q) :우선순위큐 q가 가득 찼는지 검사함
> * insert(q, x) : 우선순위큐 q에 요소 x 를 추가함
> * delete(q) : 우선순위큐로부터 가장 우선순위가 높은 요소를 삭제함과 동시에 반환함
> * find(q) : 우선순위가 가장 높은 요소를 반환함



## 종류

* 최대 우선순위 큐
* 최소 우선순위 큐



## 구현 방법

* 배열을 이용
* 연결리스트를 이용
* 힙을 이용

### 힙(heap)

* 노드의 키들이 다음 식을 만족하는 완전이진트리

* key(부모노드) $$\geq$$ key(자식노드)

  * **최대 힙**
    * 부모 노드의 키 값이 자식노드의 키 값보다 *크거나 같은* 완전 이진트리
  * **최소 힙**
    * 부모 노드의 키값이 자식 노드의 키값보다 *작거나 같은* 완전 이진트리
  * **힙의 높이**
    * $$n$$개의 노드를 가지고 있는 힙의 높이는 $$O(\log{n})$$
    * 마지막 레벨을 제외하고, 각 레벨 $$i$$에 $$2^{i-1}$$개의 노드 존재

* 구현 방법

  * **배열** : 완전 이진트리이므로 각 노드에 번호를 붙일 수 있으며, 번호를 인덱스라고 생각 함.

    * 왼쪽 자식의 인덱스 : 부모의 인덱스 * 2
    * 오른쪽 자식의 인덱스  : 부모의 인덱스 * 2 + 1
    * 부모의 인덱스 : 자식의 인덱스 / 2

    ```c
    #define _CRT_SECURE_NO_WARININGS
    #define MAX_ELEMENT 200
    #define PARENT(x)	x/2
    
    #include <stdio.h>
    #include <stdlib.h>
    typedef struct _key {
    	int key;
    }element;
    
    typedef struct _heap {
    	element heap[MAX_ELEMENT];
    	int heap_size;
    }Heap;
    
    Heap* create(void) {
    	return (Heap*)malloc(sizeof(Heap));
    }
    
    void init(Heap* h) {
    	h->heap_size = 0;
    }
    
    void up_heap(Heap* h, element item) {
    	int i = ++(h->heap_size);
    	while (i != 1 && item.key > h->heap[PARENT(i)].key) {
    		h->heap[i] = h->heap[PARENT(i)];
    		i = PARENT(i);
    	}
    	h->heap[i] = item;
    }
    
    void down_heap(Heap* h, element item) {
    	int i = ++(h->heap_size);
    	while (i != 1 && item.key < h->heap[PARENT(i)].key) {
    		h->heap[i] = h->heap[PARENT(i)];
    		i = PARENT(i);
    	}
    	h->heap[i] = item;
    }
    
    element delete_heap(Heap* h, int is_up) {
    	int parent = 1, child = 2;
    	element item, temp;
    	item = h->heap[1];
    	temp = h->heap[(h->heap_size)--];
    
    	if (is_up) {
    		while (child <= h->heap_size) {
    			if ((child < h->heap[child + 1].key) && (h->heap[child].key < h->heap[child + 1].key))
    				child++;
    
    			if (temp.key >= h->heap[child].key)
    				break;
    
    			h->heap[parent] = h->heap[child];
    			parent = child;
    			child *= 2;
    		}
    	}
    	else {
    		while (child <= h->heap_size) {
    			if ((child < h->heap[child + 1].key) && (h->heap[child].key > h->heap[child + 1].key))
    				child++;
    
    			if (temp.key <= h->heap[child].key)
    				break;
    
    			h->heap[parent] = h->heap[child];
    			parent = child;
    			child *= 2;
    		}
    	}
    	h->heap[parent] = temp;
    	return item;
    }
    
    int main(void) {
    	element e1 = { 10 }, e2 = { 5 }, e3 = { 30 };
    	element e4, e5, e6;
    	Heap* heap;
    
    	heap = create(); 	// 히프 생성
    	init(heap);	// 초기화
    
    				// 삽입
    	down_heap(heap, e1);
    	down_heap(heap, e2);
    	down_heap(heap, e3);
    
    	// 삭제
    	e4 = delete_heap(heap, 0);
    	printf("< %d > ", e4.key);
    	e5 = delete_heap(heap, 0);
    	printf("< %d > ", e5.key);
    	e6 = delete_heap(heap, 0);
    	printf("< %d > \n", e6.key);
    
    	free(heap);
    	return 0;
    }
    ```

    > up_heap 방식과 down_heap 방식 모두 구현함.
    >
    > 두 경우는 input 방식과 delete 방식이 다르다.
    >
    > 따라서 input 함수의 경우는 분리하였고, delete_heap은 매개변수 `is_up` 에 의해 delete 방식이 달라진다.



### 힙 정렬 (Heap Sort)

* 먼저 정렬해야할 n개의 요소들을 최대 힙에 삽입

  한번에 하나씩 요소를 힙에서 삭제하여 저장함. (내림차순)
  

* 먼저 정렬해야할 n개의 요소들을 최소 힙에 삽입

  한번에 하나씩 요소를 힙에서 삭제하여 저장함. (오름차순)

* 시간복잡도는 ($$O(n \log{n})$$)임.

* 가장 유용한 경우 : 가장 큰 값 몇개만 필요할 때

```c
#define _CRT_SECURE_NO_WARNINGS
#define PARENT(x) x/2
#define MAXSIZE 100

#include <stdio.h>
#include <stdlib.h>

typedef struct {
	int data;
}element;

typedef struct {
	element heap[MAXSIZE];
	int size;
}Heap;

Heap* create(void) {
	return (Heap*)malloc(sizeof(Heap));
}

void init(Heap* h) {
	h->size = 0;
}

void insert_up(Heap* h, element item) {
	int i = ++(h->size);
	while (i != 1 && item.data > h->heap[PARENT(i)].data) {
		h->heap[i] = h->heap[PARENT(i)];
		i = PARENT(i);
	}
	h->heap[i] = item;
}

element delete_heap(Heap* h) {
	int parent = 1, child = 2;
	element item, temp;
	item = h->heap[1];
	temp = h->heap[h->size--];

	while (child <= h->size) {
		if ((child < h->heap[child + 1].data) && (h->heap[child].data < h->heap[child + 1].data))
			child++;

		if (temp.data >= h->heap[child].data)
			break;

		h->heap[parent] = h->heap[child];
		parent = child;
		child *= 2;
	}
	h->heap[parent] = temp;
	return item;
}
void asc(element* h, int size) {
	Heap* space = create();
	init(space);
	for (int i = 0; i < size; i++) {
		insert_up(space, h[i]);
	}
	for (int i = 0; i < size; i++) {
		h[i] = delete_heap(space);
	}
}

int main(void) {
	element e[] = { 1,4,2,7,6,3,2,5 };
	int size = sizeof(e) / sizeof(element);
	asc(e, size);
	for (int i = 0; i < size; i++) {
		printf("%d ", e[i].data);
	}
}
```

