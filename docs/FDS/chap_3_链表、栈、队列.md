### The List ADT

```C
typedef struct Node* Nodeptr;
struct Node{
    int element;
    Nodeptr next;
};
//申请内存
Nodeptr head=(Nodeptr)malloc(sizeof(struct Node*))
```

#### Cursor Implementation of linked lists

### The Stack ADT
#### 用数列实现栈
```C
struct StackRecord{
	int capacity;
    int TopofStack;
    ElementType* Array;
};
```

- **push、pop之前必须要检查是不是合法操作**，空的不能pop，满的不能push

#### 用链表实现栈

### The Queue ADT (FIFO)

定义： 限定在一端插入（队尾），一端删除（队头）的特殊线性表

rear 指向实际队尾的元素所在的位置，front指向实际队头元素的前一个位置

`队列个数= tail-head`

```C
struct queuerecord{
    int capacity;
    int front;
    int rear;
    int size;
    Elementtype *array;
};
```

> Operations:
>
> - int isempty(Queue Q);
> - Queue CreateQueue(void);
> - void DisposeQueue(Queue Q);
> - void makeemprt(Queue Q);
> - void enqueue(elementtype x,Queue Q);
> - 

**circular queue(循环队列)**：

一样地，我们规定： head指向对头前一个，tail指向队尾

- FIFO
- 循环使用空间

​	operations

- enqueue: 
- dequeue: 



