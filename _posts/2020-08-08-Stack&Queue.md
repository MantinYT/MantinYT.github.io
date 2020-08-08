---
title: Stack&Queue
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

### 栈的应用

#### 1.括号匹配

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

#### 2.表达式求值

##### 背景知识：

- 前缀表达式

- 中缀表达式：其求值就是借用「中缀转后缀」+「后缀表达式求值」。初始化两个栈，操作数栈和运算符栈。若扫描到操作数，压入操作数栈；若扫描到运算符或界限符，则按中缀转后缀相同的逻辑压入运算符栈（期间也会弹出运算符，每当弹出一个运算符时候，就需要弹出两个操作数栈的操作数，运算后将运算结果再压回操作数栈）

- 后缀表达式的手算方法：从左往右扫描，让离操作符最近的两个操作数执行运算。

- 中缀转后缀的手算方法：

  1. 确定中缀表达式中各个运算符的运算顺序
  2. 选择下一个运算符，按「左操作数 右操作数 运算符」的方式组成一个新的操作数
  3. 如果还有运算符没被处理，重复2.
  4. "左优先"：只要左边的op能先计算，就优先。

- 中缀转后缀的机算方法：

  1. 遇到操作数。直接加入后缀表达式
  2. 遇到界限符。遇到 "(" 直接入栈；遇到 ")" 则依次弹出栈内运算符并加入后缀表达式，直到弹出 "(" 为止。"(" 不加入表达式。
  3. 遇到运算符。依次弹出栈中优先级高于等于当前运算符的所有运算符，并加入后缀表达式，若碰到 "(" 或栈空则停止。之后再把当前运算符入栈。==》 * / 高于 + -
  4. 处理完所有字符后，将栈中剩余运算符依次弹出，并加入后缀表达式。

- 后缀求解表达式值：

  ​	顺序扫描表达式：若该项是操作数，则入栈。若该项是操作符，则连续退栈两个操作数Y和X，运算X opertate Y，将结果入栈。



### 涉及到的基本操作

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

## 队列

### 队列顺序存储结构类型描述：

```c
#define MaxSize 10
typedef strcut{
    ElemType data[MaxSize];
    int front, rear;	//队头指针和队尾指针
}SqQueue;
```

### 链队存储结构类型描述：

```c
typedef struct LinkNode{	//链队结点
    ElemType data;
    struct LinkNode *next;
}LinkNode;
typedef struct{		链队
    LinkNode *front, *rear;		//队头和队尾指针
}LinkQueue;
```

### 队列的应用

#### 1.树的层次编列

#### 2.图的广度优先遍历

------

等复习到再更😋