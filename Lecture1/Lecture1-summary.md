# ACMM协会第一周讲座总结 

---

## 基本语句

### 条件语句

- **if**语句

结构：
```C++
if (表达式) 语句;
else if (表达式) 语句;
else 语句;
```
- **switch**语句

结构：
```C++
switch(表达式){
    case 常量表达式1:语句1;break;
    case 常量表达式2:语句2;break;
    …
    case 常量表达式n:语句n;break;
    default:语句n+1;
}
```

条件语句的作用便是通过表达式进行判定，选择所要执行的代码块（或是否要执行代码块）。

### 循环语句

- **for**语句

结构：
```C++
for(初始语句;条件语句;控制语句){循环体;}
```
- **while**语句

结构：
```C++
while(条件){语句;}
```

- **do-while**语句

结构：
```C++
do{
    语句;
}while(条件);
```

while语句和do-while语句的区别便在于while语句先判断条件决定是否进入循环体，而do-while语句则是先运行循环体再通过条件判断是否跳出。

## 位运算

- 或（**|**）运算

运算法则：
```C++
x = 1|3;//x == 3
```
因为1的二进制表达为![](http://latex.codecogs.com/gif.latex?~0001~)，3的二进制表达为![](http://latex.codecogs.com/gif.latex?~0011~)。其中或运算表示，若有一个数在当前位为![](http://latex.codecogs.com/gif.latex?~1~)，则当前位为![](http://latex.codecogs.com/gif.latex?~1~)。
以此类推： 

![](http://latex.codecogs.com/gif.latex?~2|1=3~)

![](http://latex.codecogs.com/gif.latex?0010~|~0001~=~0011)

- 与（**&**）运算

运算法则：
```C++
x = 1&3;//x == 1
```
![](http://latex.codecogs.com/gif.latex?0001~\\&~0011~=~0001)

与运算表示，若两个数在当前位都为![](http://latex.codecogs.com/gif.latex?~1~)，则当前位为![](http://latex.codecogs.com/gif.latex?~1~)，否则为![](http://latex.codecogs.com/gif.latex?~0~)。

- 异或（**^**）运算

运算法则：
```C++
x = 1^3;//x == 2
```
![](http://latex.codecogs.com/gif.latex?0001~^\\wedge~~0011~=~0010)
异或运算表示，若两个数在当前位的数字不相同，则当前位为![](http://latex.codecogs.com/gif.latex?~1~)，否则为![](http://latex.codecogs.com/gif.latex?~0~)。

位运算在算法竞赛中较为常用，因为它可以节省大量的运算时间。

比如我们可以用下方代码交换两个数

```C++
int a=10,b=12; //a=1010,b=1100; 
a=a^b; //a=0110,b=1100; 
b=a^b; //a=0110,b=1010; 
a=a^b; //a=1100;b=1010; 
```

## 数组

> 简单定义：
> 数组（array）由一系列类型相同的元素构成

结构：
```C++
类型说明符 数组名 [常量表达式];
```

## 时空复杂度

### 空间复杂度
![](http://latex.codecogs.com/gif.latex?~1mb=1024kb~)

![](http://latex.codecogs.com/gif.latex?~1kb=1024b~)

![](http://latex.codecogs.com/gif.latex?~long%20long=8b~)

![](http://latex.codecogs.com/gif.latex?~int=4b~)

![](http://latex.codecogs.com/gif.latex?~double=8b~)

通过简要计算程序中所使用的变量数以及变量大小可以大致算出程序要使用多少内存。一般只需要粗略估计内存使用量，符合题目要求即可。


### 时间复杂度

大致估算：

直接测量程序运行时间；

通过将程序中的每层循环的复杂度相乘，得到大致复杂度；

主定理：

> 设![](http://latex.codecogs.com/gif.latex?a~\\geq%201)和![](http://latex.codecogs.com/gif.latex?b~\\gt%201)为常数，设![](http://latex.codecogs.com/gif.latex?f(n))为一函数，![](http://latex.codecogs.com/gif.latex?T(n))由递归式  
 ![](http://latex.codecogs.com/gif.latex?T(n)~=~aT(\\frac%20{n}{b})~+~f(n))  
 其中![](http://latex.codecogs.com/gif.latex?\\frac%20{n}{b})指![](http://latex.codecogs.com/gif.latex?\\lceil%20\\frac%20{n}{b}\\rceil%20)和![](http://latex.codecogs.com/gif.latex?\\lfloor%20\\frac%20{n}{b}\\rfloor%20)，可以证明，略去上下去整不会对结果造成影响。那么![](http://latex.codecogs.com/gif.latex?T(n))可能有如下的渐进界  
 (1)若![](http://latex.codecogs.com/gif.latex?f(n)~\\lt%20~n^\\log%20{}\\frac%20{n}{b})，且是多项式的小于。即  
 ![](http://latex.codecogs.com/gif.latex?\\exists%20\\varepsilon%20\\gt%200)，有![](http://latex.codecogs.com/gif.latex?f(n)~=~O(n^\\log%20{}\\frac%20{n}{b}-\\varepsilon%20))，则![](http://latex.codecogs.com/gif.latex?T(n)~=~\\Theta%20\\left%20(n^\\log%20{}\\frac%20{n}{b}\\right%20))  
 (2)若![](http://latex.codecogs.com/gif.latex?f(n)~=~n^\\log%20{}\\frac%20{n}{b})，则![](http://latex.codecogs.com/gif.latex?T(n)~=~\\Theta%20\\left((\\log%20n)~n^\\log%20{}\\frac%20{n}{b}\\right%20))  
 (3)若![](http://latex.codecogs.com/gif.latex?f(n)~\\gt%20~n^\\log%20{}\\frac%20{n}{b})，且是多项式的大于。即  
 ![](http://latex.codecogs.com/gif.latex?\\exists%20\\varepsilon%20\\gt%200)，有![](http://latex.codecogs.com/gif.latex?f(n)~=~\\Omega%20\\left(n^\\log%20{}\\frac%20{n}{b}+\\varepsilon%20\\right))，且对![](http://latex.codecogs.com/gif.latex?\\forall%20~c\\lt%201)与所有足够大的![](http://latex.codecogs.com/gif.latex?n)，  
有![](http://latex.codecogs.com/gif.latex?af(\\frac%20{n}{b})\\leq%20cf(n))，则![](http://latex.codecogs.com/gif.latex?T(n)=\\Theta%20\\bigl%20(f(n)\\bigr%20))

关于时间复杂度会在离散课程中讲到

## 递推与递归

### 递推

定义：
递推算法是一种用若干步可重复运算来描述复杂问题的方法。
递推是序列计算中的一种常用算法。通常是通过计算机前面的一些项来得出序列中的指定项的值

#### 斐波那契数列

>例题：
斐波那契数列定义为：
![](http://latex.codecogs.com/gif.latex?F(0)=0,~F(1)=1,~F(n)=F(n-1)+F(n-2)~~~~~(n\\geqslant%202,n\\in%20N^+)~)
求解斐波那契数列第![](http://latex.codecogs.com/gif.latex?n)项。

> 输入：

> 一个非负整数![](http://latex.codecogs.com/gif.latex?n)。

> 输出：

> 斐波那契数列第![](http://latex.codecogs.com/gif.latex?n)项。

示例代码：
```C++
#include<cstdio>
using namespace std;
int main() {
    int n,fib[100];
    scanf("%d",&n);
    fib[0]=1;
    fib[1]=1;
    for (int i=2;i<=n;i++) fib[i]=fib[i-1]+fib[i-2];
    printf("%d\n",fib[n]);
}
```
这里我们充分利用了定义以及递推的思想，用已知的&F(0)&与&F(1)&，将前一百项均推出来，再输出我们想求的项的值。

### 递归

定义：
程序调用自身的编程技巧称为递归，通常把一个大型复杂的问题层层转化为一个与原问题相似的规模较小的问题来求解。

#### 斐波那契数列

递归和递推虽然看起来差不多，但是其本质并不相同，我们可以看一下上面的斐波那契数列的递归形式表达。

```C++
int fib(int n)
{
    if(n<2) return n;
    else return fib(n-1)+fib(n-2);
}
```
这里我们则是把![](http://latex.codecogs.com/gif.latex?F(n))这个大问题化为了![](http://latex.codecogs.com/gif.latex?F(n-1)+F(n-2))这样更小的问题，一步步把大问题化为小问题直至我们能够求出为止。

#### 汉诺塔问题

>有三根相邻的柱子，标号为A,B,C，A柱子上从下到上按金字塔状叠放着![](http://latex.codecogs.com/gif.latex?n)个不同大小的圆盘，要把所有盘子一个一个移动到柱子B上，并且每次移动同一根柱子上都不能出现大盘子在小盘子上方，请问至少需要多少次移动。

>输入

>圆盘个数![](http://latex.codecogs.com/gif.latex?n)。

>输出

>汉诺塔移动过程

示例代码：

```C++
#include<cstdio>
using namespace std;
void hanoi(int x,int A,int B){
//x表示所剩圆盘数量 ,A表示把盘子从哪个位置（这里我们假设为p位置），B表示移到哪个位置（这里我们假设为q位置）。
    if (!x) return;
    //如果x==0，即没有圆盘需要移动时，不再运行下面内容
    hanoi(x-1,A,3-A-B);
    //把p上n-1个圆盘移动到除p，q以外的那个位置（我们假设该位置为m）
    printf("%d:%c->%c\n",x,'A'+A,'A'+B);
    //当p上的n-1个圆盘均移动到了m(上一步完成后)，输出把当前p上仅存的那个圆盘移动到q的操作
    hanoi(x-1,3-A-B,B);
    //把m上n-1个盘子移动到q
    //当n=1时，两条递归语句都不会执行有效内容，输出语句会输出把最后一个圆盘从p移动到q的操作
}
int main() {
    int n;
    scanf("%d",&n);
    hanoi(n,0,1);
    //这里0 1代表从A移到B，'A'+0='A','A'+1='B'
}
```
汉诺塔问题的递归解法便是将把A上![](http://latex.codecogs.com/gif.latex?n)个圆盘移动到B的问题化为把A上![](http://latex.codecogs.com/gif.latex?n-1)个圆盘移动到C，再把A上最大的圆盘移动到B，最后把C上![](http://latex.codecogs.com/gif.latex?n-1)个圆盘移动到B的问题。

关于汉诺塔问题最优解步数我们还可以通过下方的数学数学公式：

![](http://latex.codecogs.com/gif.latex?a[n]~=~2*a[n-1]+1)

![](http://latex.codecogs.com/gif.latex?a[1]~=~1)

![](http://latex.codecogs.com/gif.latex?a[n]~=~2^n~-~1)

