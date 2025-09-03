常考考点： 

对于n个顶点的无向图，若连通，最少有`n-1`条边，若不连通，最多C(n-1，2)条边

对于n个顶点的强连通图，最少有n条边（形成回路）

> 有向图的强连通： 从v到w和从w到v之间都有路径，则称这两个顶点强连通	
>
> 强连通图：任意一对顶点都是强连通的
>
> 生成树： 是包含图中所有顶点的一个极小连通子图

#### 图的存储

##### 邻接矩阵（空间复杂度$O(n^2)$）

```	C
#define max 100//顶点数目最大值
typedef struct{
	char vex[max];
    int edge[max][max];
    int vexnum,arcnum;
}MGraph;
```

也可以用邻接矩阵法存储带权图，将1改为权重

##### 邻接表（顺序+链式存储）

```C
//边
typedef struct ArcNode{
	int adjvex;//指向哪个节点
	struct ArcNode* next;
}ArcNode;
//顶点
typedef struct VNode{
	VertexType data;
    ArcNode* first;
}VNode,AdjList[max];
//用邻接表存储的图
typedef struct{
	Adjlist vertices;
    int vexnum,arcnum;
}ALGraph;
```



##### 拓扑排序

```C
void Toposort(Graph G){
    
}
```

