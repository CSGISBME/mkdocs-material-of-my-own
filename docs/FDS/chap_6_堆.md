堆的定义： 是一个完全二叉树、有堆序性（可以分为大根堆、小根堆）

一个高度为h的完全二叉树的节点数n在$2^h \text{和}2^{h+1}$之间

| 0    | 1    | 2    | 3    | 4    | 5    |
| ---- | ---- | ---- | ---- | ---- | ---- |
|      | A    | B    | C    | D    | E    |

【lemma】
$$
index\ of\ parent(i)=
\begin{cases}
\lfloor i/2 \rfloor,&if\ i>1 \\
None,&if\ i=1
\end{cases}
$$
$$
index\ of\ lchild(i)=
\begin{cases}
2i,&if\ 2i\leq n \\
None,&if\ 2i \gt n
\end{cases}
$$

$$
index\ of\ rchild(i)=
\begin{cases}
2i+1,&if\ 2i+1\leq n\\
None,&if\ 2i+1 \gt n
\end{cases}
$$

```C

```



堆的基本操作： 上滤、下滤（根节点向下动）
