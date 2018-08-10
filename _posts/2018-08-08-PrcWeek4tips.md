---
title: 关于第四周的一点小结
date: 2018-08-07 12:33:44-0800
categories:
-   PYTHON123
tags:
- WeekFour
---
## 关于第四周的一点小结
### 二分支语句:  
<语句> if <条件> else <语句> 紧凑形式。  
### 异常处理:  
try:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句1>  
except:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句2>  
eles:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句3>  **else对应语句3在不发生异常时执行**  
finally:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句4>  **finally对应语句4一定执行**  

### 遍历循环:  
- 计数遍历循环:  
for i in range(M,N,[K])  
- 字符串遍历循环:  
for c in s:  
s是字符串,遍历字符串每个字符,产生循环  
-列表遍历循环:  
ls是一个列表,遍历其中每个元素,产生循环  
- 文件遍历循环:  
for line in fi:  
fi是一个文件标识符,遍历其中每行,产生循环  
- 循环的扩展:  
for <变量> in <遍历结构>:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句1>  
else:  
&nbsp;&nbsp;&nbsp;&nbsp;<语句2>  

>当循环语句没有被break语句退出时,执行else语句块,else在这里作为"正常"完成循环的奖励。  

## 蒙特卡洛方法思想:  
**投点法计算圆周率参数**
