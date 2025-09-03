### 基础知识

#### 树的实现

- 任意的树

  ```C
  struct TreeNode{
  	int element;
    struct TreeNode* firstchild;
    struct TreeNode* nextsibling;
  }
  ```

- 二叉树

  ```C
  struct TreeNode{
  	int element;
    struct TreeNode* lchild;
  	struct TreeNode* rchild;
  };
  ```

  二叉树可以和任何树相互转化，转化后连接的顺序不变，parent和sibling的关系会改变

#### 树的遍历

- `preorder`: 根左右
- `inorder`: 左根右
- `postorder`:左右根
- `levelorder`:每一层从左到右，从第一层到最后一层

#### 线索二叉树（Threaded binary trees）

线索： 指向结点前驱、后继的指针

```C
typedef struct TBNode{
	  char data;
    int LTag,Rtag;//LTag=0 指向左孩子 LTag=1 指向前驱
    struct TBNode* lchild;
    struct TBNode* rchild;
}TBNode;
```

若左指针为空，左指针指向前驱；若右指针为空，右指针指向后驱；

有先序线索二叉树、中序线索二叉树

```C
//以中序为例，介绍线索化二叉树算法


```

#### 经典题型

`给定前序中序找`



#### BST(binary search tree)

##### 定义

1.是二叉树

2.左孩子< 根< 右孩子

3.左右子树都是BST

##### 操作

###### 寻找

```C
//递归法
Position Find(ElementType X,SearchTree T){
	if(T==NULL){
		return NULL;
    if(X<T->Left){
		return Find(X,T->Left);
    }else if(x>T->Right){
		return Find(X,T->Right);
    }else{
		return T;
    }
}
//循环法
Position Find(ElementType X,SearchTree T){
	while(T){
		if(X==T->Element){
			return T;
        }else if(X<T->Element){
          T=T->Left;
        }else{
			T=T->right;
        }
    }
	return NULL;
}
```

###### 找最小
```C
Position FindMin(SearchTree T){
  if(T==NULL){
    return T;
  }else{
   if(T->left==NULL){
    return T;
  }else{
    return FindMin(T->left)
  }
  }
}
```
###### 找最大
```C
Position FindMax(SearchTree T){
	if(T==NULL)
        while(T->Right!=NULL){
				T=T->Right;
        }
    return T;
}

```

###### 插入

```C
SearchTree  Insert( ElementType X, SearchTree T ) 
{ 
 	if ( T == NULL ) { /*传入的是空结点，说明找到了位置，或者树本来就是空的*/
		T = malloc( sizeof( struct TreeNode ) ); 
	else { 
	   		T->Element = X; 
	   		T->Left = T->Right = NULL; } 
      	}  
    else  /* If there is a tree */
 	if ( X < T->Element ) 
	   T->Left = Insert( X, T->Left ); 
	else 
	   if ( X > T->Element ) 
	      T->Right = Insert( X, T->Right ); 
	   /* Else X is in the tree already; we'll do nothing */ 
    return  T;   /* Do not forget this line!! */ 
}
```

###### 删除

```C
SearchTree  Delete( ElementType X, SearchTree T ) 
{    Position  TmpCell; 
      if ( T == NULL )   Error( "Element not found" ); 
      else  if ( X < T->Element )  /* Go left */ 
	    T->Left = Delete( X, T->Left ); 
               else  if ( X > T->Element )  /* Go right */ 
	           T->Right = Delete( X, T->Right ); /*到这边为止都是在找被删的结点*/
	         else  /* 找到了被删的结点 */ 
	           if ( T->Left && T->Right ) 
	           {  /* 两个孩子的情况，把结点替换成右边最小的 */ 
	               TmpCell = FindMin( T->Right ); 
	               T->Element = TmpCell->Element; 
	               T->Right = Delete( T->Element, T->Right ); 
	               /*这边需要把找到的右节点给删了，个人觉得直接找的时候就删了会更好一点*/
	           } /* End if */
	           else 
	           {  /* 只有一个孩子或没有孩子 */ 
	               TmpCell = T; 
	               if ( T->Left == NULL ) /*左边如果是空的，就让右边结点代替*/
		         		T = T->Right; 
	               else  if ( T->Right == NULL )  /*右边结点是空的，就让左边结点代替*/
	               		T = T->Left; 
	               free( TmpCell );  
	           }  /* 这样1个和0个孩子都没有问题*/
      return  T; 
}
```

