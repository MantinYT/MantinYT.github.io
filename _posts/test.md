```c
//preorder
void PreOrder(BiTree T){
    if(T==null)
        return false;
    else{
        visit(T);
        PreOrder(T->lchild);
        PreOrder(T->rchild);
    }
}
```

```c
//nonrecursive
void PreOrder2(BiTree T){
    InitStack(S);
    BiTNode p = T;
   while(p || !EmptyStack(S)){
       if(p){
           visit(p);
           push(S,p);
           p = p->lrchild;
       }else{
           pop(S);
           p = p->rchild;
       }
       
   }
}
```



```c
//postorder
void PostOrder(BiTree T){
     if(T==null)
        return false;
    else{
        PostOrder(T->lchild);
        PostOrder(T->rchild);
        visit(T);
    }
}
```

```c
//nonrecursive
void PostOrder2(BiTree T){
    InitStack(S);
    BiTNode p = T;
    BiTNode pre = null;//指向最近访问的结点
    while(p || !EmptyStack(S)){
        if(p){
            push(S,p);
            p = p->lchild;
        }else{
            GetTop(S,p);
            if(p->rchild!=null && p->rchild!=pre){
                p = p->rchild;
                push(S,p);
                p = p->lchild;
            }else{
                pop(S,p); 
                visit(p);
                pre = p;
                p = null;
            }
        }
    }
}
```



```c
//inorder
void InOrder(BiTree T){
    if(T==null)
        return false;
    else{
        InOrder(T->lchild);
        visit(T);
        InOrder(T->rchild);
    }
}
```

```c
//nonrecursive
void InOrder2(BiTree T){
    InitStack(S);
    BiTNode p = T;
    while(p || !EmptyStack(S)){
        if(p){
            push(S,p);
            p = p->rchild
        }else{
            pop(S,p);
            visit(p);
            p = p->rchild;
        }
    }
}
```

```c
//levelorder
void levelOrder(BiTree T){
    InitQueue(Q);
    BiTNode p = T;
    EnQueue(Q,p);
    while(!EmptyQueue(Q)){
        DeQueue(Q,p);
        if(p->lchild!=null)
            EnQueue(Q,p);
        if(p->rchild!=null)
            EnQueue(Q,p);
    }
}
```

```c
//Depthfirst
void DepthFirst(Graph G){
    for(int i=0; i<G.vexnum; i++){
        visited[i] = false;
    }
    for(int j=0;j<G.vexnum; j++){
        if(!visited[j])
            DFS(Graph,j)
    }
}

void DFS(Graph G, int v){
    int w;
    visit(v);
    visited[v] = true;
    while(w=FirstNeighbor(G,v);w>=0;w=NextNeighbor(G,v,w)){
        if(!visited[w])
            DFS(D,w);
    }
}
```

```c
//widthfirst
void widthFirst(Graph G){
     for(int i=0; i<G.vexnum; i++){
        visited[i] = false;
    }
    for(int j=0;j<G.vexnum; j++){
        if(!visited[j])
            WFS(Graph,j)
    }
}

void WFS(Graph G, int v){
    int w;
    InitQueue(Q);
    EnQueue(Q,v);
    while(!EmptyQueue(Q)){
        DeQueue(Q,v);
        visit(v);
        visited[k] = true;
        for(w=FirstNeighbor(G,v);w>=0;w=NextNeighbor(G,v,w))
    }{
        if(!visited[w]){
            visit(w);
            visited[w] = true;
            EnQueue(Q,w);
        }
            
    }
}
```

#### 2016.algorithm1

```c
void movearray(int array[], int left, int right, int arraysize){
    int temp;
    if(left>=right || right>=arraysize){
        return;
    }
    for(int i=left,int j=right; i<j; i++,j--){
        temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}
void exchange(int array[],int m,int n){
    movearray(array, 0,m-1,m);
    movearray(array,2m,n-1,m);
    movearray(array,0,n-1,n);
}
```

#### 2019.brif5-wdp20

> 主元素
>
> 寻找可能的主元素
>
> 判断是否真的是主元素
>
> time consuming  n,space consuming 1

```c
int Majority(int A[], int n){
    int i,maj, count=1;		//maj保存候选主元素，count负责计数
    c = A[0];		//选A[0]为候选主元素
    for(int i=1;i<n;i++){		//查找候选主元素
        if(A[i]==c){
            count++;
        }else{		//处理不是主元素的情况
            if(count>0)
                count--;
            else{		//更换主元素
                c = A[i];
                count = 1;
            }//endelse
        }//endelse
    }//endfor
    if(count>0)		//统计候选主元素的实际出现次数
        for(i=count=0;i<n;i++)
            if(A[i]=c)
                count++;
    if(count>n/2)		//确认主元素
        return c;
    else
        return -1;		//不存在主元素
}
```



#### 2019.algorithm1x

```c
void evenodd(ElemType A[],int n){
    int i=0,j=0;
    for(j<=n-1){
        if(A[j]%2!=0){
            swap(A[i],A[j]);
            i++;
            j++;
        }
        else
            j++;
    }
}
```



#### 2019.algorithm2

> bst

```c
bool BST_Insert(BiTree &T,ElemType k){
    if(T==null){
        T=(BiTree)malloc(sizeof(BiTNode));
        T->data = k;
        T->lchild=T->rchild=null;
        return true;
    }
    else if(k==T->data)
        return false;
    else if(k<T->data)
        return BST_Insert(T->lchild,k);
    else
        return BST_Insert(T->rchild,k);
}
```

```c
bool BST_Delete(BiTree &T,ElemType k){
    BiTNode p = T;
    BiTNode parent = null;
    if(T==null)
        return false;
    while(p!=null){
        if(k<p->data)
            parent = p;
            p = p->lchild;
        else if(k>p->data)
            parent = p;
            p = p->rchild;
        else
            break;
    }
    //空树情况
    if(p==null)
        return false;
    //只有左子树为空
    if(p->lchild==null && p->rchild!=null){
        if(parent!=null){
            if(parent.lchild == p)
                parent.lchild = p->rchild;
            else
                 parent.rchild = p->rchild;
        }
        else
            T = p->rchild;
    }
    //只有右子树为空
      if(p->rchild==null && p->lchild!=null){
        if(parent!=null){
            if(parent.lchild == p)
                parent.lchild = p->lchild;
            else
                 parent.rchild = p->lchild;
        }
        else
            T = p-lrchild;
    }
    //左右子树均存在，选择直接后继代替
    else{
        BiTNode ReplaceNode = p->rchild;
        BiTnode RepalceparentNode = p;
        while(RepalceNode->lchild=null){
            RepalceparentNode = ReplaceNode;
            RepalceNode=ReplaceNode->lchild;
        }
        //替换结点不存在左孩子时
        if(ReplaceparentNode == p)
            ReplaceparentNode->rchild = ReplaceNode->rchild;
        else
            ReplaceparentNode->lchild = ReplaceNode->rchild;
        //更新对应的值
        p->data = ReplaceNode->data;
    }
}
```



#### 调整满二叉树的叶子结点

```c
void exleaves(BiTree T){
    BiTNode p = T;
    InitQueue(Q);
    EnQueue(Q,p);
    while(!QueueEmpty(Q)){
        if(p->lchild->lchild!=null){
            DeQueue(p);
            EnQueue(p->lrchild);
            EnQueue(p->rchild);
        }
        else
            break;
    }
    while(!QueueEmpty(Q)){
        DeQueue(Q,p);
        swap(p->lchild,p->rchild);
    }
}
```

#### 2016.os

```c
semphore mutex = 1;//互斥访问缓冲区
semphore full = 0;
semphore empty[k] = [0,0,....,0];
int i = 0;
bool result = false;
int countprod = 0;
int countcons = 0;
semphore mutexdata = 1;//
semphore dataprotect[M] = [0,0,...,0];
productor{
    生产；
    p(empty);
    p(mutex);
    p(mutexdata)
    while(i<countcons){
        if(dataprotect[i]==1)
            result = true;
        else{
            result = false;
            break;
        }    
    }
    if(result==false){
        countprod++;
    }else{
        
    }
    
    v(mutexdata);
    放入产品；
    v(mutex);
    v(full);
}

```

