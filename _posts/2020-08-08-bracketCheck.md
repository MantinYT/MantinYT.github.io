---
title: bracketCheck
date: 2020-08-08 20:17-0800
categories:
-   DataStructure
tags:
- DataStrcture Stack&Queue

---

## 栈

### 顺序栈结构类型描述

```c
#define MaxSize 10
typedef struct{
    char data[MaxSize];
    int top;
}SqStack;
```

### 共享栈结构类型描述

```c
#define MaxSize 10
typedef struct{
    char data[MaxSize];
    int top0;
    int top1;
}ShStack;
//栈满条件 top0+1 == top1;
//栈空条件：top0 == -1 && top1 == MaxSize
```

### 链栈结构类型描述

```c
#define MaxSize 10
typedef struct Linknode{
    ElemType data;
    struck Linknode *next;
}*LiStack;
```



### 括号匹配

```c
bool bracketCheck(char str[], int length){
    SqStack S;
    InitStack(S);
    for(int i=0; i<length; i++){
        //扫描的左括号则入栈
        if(str[i] == '(' || str[i] == '[' || str[i] == '{'){
            Push(S, str[i]);
        }else{
            if(StackEmpty(S)){	//扫描到右括号但栈空
                return false;	//匹配失败
            }
            char topElem;
            Pop(S, topElem);	//栈顶元素出栈
            if(str[i] == ')' && topElem!='(')
                return false;
            if(str[i] == ']' && topElem!='[')
                return false;
            if(str[i] == '}' && topElem!='{')
                return false
        }
    }
    return StackEmpty(S);	//检索完毕后若栈空则匹配成功
}
```



## 涉及到的基本操作

> for practice😀

### 初始化栈

```c
void InitStack(SqStack &S){
    int top = -1;
}
```



### 判断栈空

```c
bool StackEmpty(SqStack S){
    if(S.top == -1)
        return true;
    else
        return false;
}
```



### 入栈

```c
bool Push(SqStacj &S, char x){
    if(S.top+1 == MaxSize)	//判断是否栈满
        return false;
    S.data[++S.top] = x;
    return true;
}
```



### 出栈

```c
bool Pop(SqStack &S, char &x){
    if(StackEmpty(S))	//判断是否栈空
        return false;
    x = S.data[S.top--];
    return true;
}
```
