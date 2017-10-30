# ACMMЭ���һ�ܽ����ܽ� 

---

## �������

### �������

- **if**���

�ṹ��
```C++
if (���ʽ) ���;
else if (���ʽ) ���;
else ���;
```
- **switch**���

�ṹ��
```C++
switch(���ʽ){
    case �������ʽ1:���1;break;
    case �������ʽ2:���2;break;
    ��
    case �������ʽn:���n;break;
    default:���n+1;
}
```

�����������ñ���ͨ�����ʽ�����ж���ѡ����Ҫִ�еĴ���飨���Ƿ�Ҫִ�д���飩��

### ѭ�����

- **for**���

�ṹ��
```C++
for(��ʼ���;�������;�������){ѭ����;}
```
- **while**���

�ṹ��
```C++
while(����){���;}
```

- **do-while**���

�ṹ��
```C++
do{
    ���;
}while(����);
```

while����do-while�������������while������ж����������Ƿ����ѭ���壬��do-while�������������ѭ������ͨ�������ж��Ƿ�������

## λ����

- ��**|**������

���㷨��
```C++
x = 1|3;//x == 3
```
��Ϊ1�Ķ����Ʊ��Ϊ![](http://latex.codecogs.com/gif.latex?~0001~)��3�Ķ����Ʊ��Ϊ![](http://latex.codecogs.com/gif.latex?~0011~)�����л������ʾ������һ�����ڵ�ǰλΪ![](http://latex.codecogs.com/gif.latex?~1~)����ǰλΪ![](http://latex.codecogs.com/gif.latex?~1~)��
�Դ����ƣ� 

![](http://latex.codecogs.com/gif.latex?~2|1=3~)

![](http://latex.codecogs.com/gif.latex?0010~|~0001~=~0011)

- �루**&**������

���㷨��
```C++
x = 1&3;//x == 1
```
![](http://latex.codecogs.com/gif.latex?0001~\\&~0011~=~0001)

�������ʾ�����������ڵ�ǰλ��Ϊ![](http://latex.codecogs.com/gif.latex?~1~)����ǰλΪ![](http://latex.codecogs.com/gif.latex?~1~)������Ϊ![](http://latex.codecogs.com/gif.latex?~0~)��

- ���**^**������

���㷨��
```C++
x = 1^3;//x == 2
```
![](http://latex.codecogs.com/gif.latex?0001~^\\wedge~~0011~=~0010)
��������ʾ�����������ڵ�ǰλ�����ֲ���ͬ����ǰλΪ![](http://latex.codecogs.com/gif.latex?~1~)������Ϊ![](http://latex.codecogs.com/gif.latex?~0~)��

λ�������㷨�����н�Ϊ���ã���Ϊ�����Խ�ʡ����������ʱ�䡣

�������ǿ������·����뽻��������

```C++
int a=10,b=12; //a=1010,b=1100; 
a=a^b; //a=0110,b=1100; 
b=a^b; //a=0110,b=1010; 
a=a^b; //a=1100;b=1010; 
```

## ����

> �򵥶��壺
> ���飨array����һϵ��������ͬ��Ԫ�ع���

�ṹ��
```C++
����˵���� ������ [�������ʽ];
```

## ʱ�ո��Ӷ�

### �ռ临�Ӷ�
![](http://latex.codecogs.com/gif.latex?~1mb=1024kb~)

![](http://latex.codecogs.com/gif.latex?~1kb=1024b~)

![](http://latex.codecogs.com/gif.latex?~long%20long=8b~)

![](http://latex.codecogs.com/gif.latex?~int=4b~)

![](http://latex.codecogs.com/gif.latex?~double=8b~)

ͨ����Ҫ�����������ʹ�õı������Լ�������С���Դ����������Ҫʹ�ö����ڴ档һ��ֻ��Ҫ���Թ����ڴ�ʹ������������ĿҪ�󼴿ɡ�


### ʱ�临�Ӷ�

���¹��㣺

ֱ�Ӳ�����������ʱ�䣻

ͨ���������е�ÿ��ѭ���ĸ��Ӷ���ˣ��õ����¸��Ӷȣ�

������

> ��![](http://latex.codecogs.com/gif.latex?a~\\geq%201)��![](http://latex.codecogs.com/gif.latex?b~\\gt%201)Ϊ��������![](http://latex.codecogs.com/gif.latex?f(n))Ϊһ������![](http://latex.codecogs.com/gif.latex?T(n))�ɵݹ�ʽ  
 ![](http://latex.codecogs.com/gif.latex?T(n)~=~aT(\\frac%20{n}{b})~+~f(n))  
 ����![](http://latex.codecogs.com/gif.latex?\\frac%20{n}{b})ָ![](http://latex.codecogs.com/gif.latex?\\lceil%20\\frac%20{n}{b}\\rceil%20)��![](http://latex.codecogs.com/gif.latex?\\lfloor%20\\frac%20{n}{b}\\rfloor%20)������֤������ȥ����ȥ������Խ�����Ӱ�졣��ô![](http://latex.codecogs.com/gif.latex?T(n))���������µĽ�����  
 (1)��![](http://latex.codecogs.com/gif.latex?f(n)~\\lt%20~n^\\log%20{}\\frac%20{n}{b})�����Ƕ���ʽ��С�ڡ���  
 ![](http://latex.codecogs.com/gif.latex?\\exists%20\\varepsilon%20\\gt%200)����![](http://latex.codecogs.com/gif.latex?f(n)~=~O(n^\\log%20{}\\frac%20{n}{b}-\\varepsilon%20))����![](http://latex.codecogs.com/gif.latex?T(n)~=~\\Theta%20\\left%20(n^\\log%20{}\\frac%20{n}{b}\\right%20))  
 (2)��![](http://latex.codecogs.com/gif.latex?f(n)~=~n^\\log%20{}\\frac%20{n}{b})����![](http://latex.codecogs.com/gif.latex?T(n)~=~\\Theta%20\\left((\\log%20n)~n^\\log%20{}\\frac%20{n}{b}\\right%20))  
 (3)��![](http://latex.codecogs.com/gif.latex?f(n)~\\gt%20~n^\\log%20{}\\frac%20{n}{b})�����Ƕ���ʽ�Ĵ��ڡ���  
 ![](http://latex.codecogs.com/gif.latex?\\exists%20\\varepsilon%20\\gt%200)����![](http://latex.codecogs.com/gif.latex?f(n)~=~\\Omega%20\\left(n^\\log%20{}\\frac%20{n}{b}+\\varepsilon%20\\right))���Ҷ�![](http://latex.codecogs.com/gif.latex?\\forall%20~c\\lt%201)�������㹻���![](http://latex.codecogs.com/gif.latex?n)��  
��![](http://latex.codecogs.com/gif.latex?af(\\frac%20{n}{b})\\leq%20cf(n))����![](http://latex.codecogs.com/gif.latex?T(n)=\\Theta%20\\bigl%20(f(n)\\bigr%20))

����ʱ�临�ӶȻ�����ɢ�γ��н���

## ������ݹ�

### ����

���壺
�����㷨��һ�������ɲ����ظ�������������������ķ�����
���������м����е�һ�ֳ����㷨��ͨ����ͨ�������ǰ���һЩ�����ó������е�ָ�����ֵ

#### 쳲���������

>���⣺
쳲��������ж���Ϊ��
![](http://latex.codecogs.com/gif.latex?F(0)=0,~F(1)=1,~F(n)=F(n-1)+F(n-2)~~~~~(n\\geqslant%202,n\\in%20N^+)~)
���쳲��������е�![](http://latex.codecogs.com/gif.latex?n)�

> ���룺

> һ���Ǹ�����![](http://latex.codecogs.com/gif.latex?n)��

> �����

> 쳲��������е�![](http://latex.codecogs.com/gif.latex?n)�

ʾ�����룺
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
�������ǳ�������˶����Լ����Ƶ�˼�룬����֪��&F(0)&��&F(1)&����ǰһ������Ƴ����������������������ֵ��

### �ݹ�

���壺
�����������ı�̼��ɳ�Ϊ�ݹ飬ͨ����һ�����͸��ӵ�������ת��Ϊһ����ԭ�������ƵĹ�ģ��С����������⡣

#### 쳲���������

�ݹ�͵�����Ȼ��������࣬�����䱾�ʲ�����ͬ�����ǿ��Կ�һ�������쳲��������еĵݹ���ʽ��

```C++
int fib(int n)
{
    if(n<2) return n;
    else return fib(n-1)+fib(n-2);
}
```
�����������ǰ�![](http://latex.codecogs.com/gif.latex?F(n))��������⻯Ϊ��![](http://latex.codecogs.com/gif.latex?F(n-1)+F(n-2))������С�����⣬һ�����Ѵ����⻯ΪС����ֱ�������ܹ����Ϊֹ��

#### ��ŵ������

>���������ڵ����ӣ����ΪA,B,C��A�����ϴ��µ��ϰ�������״������![](http://latex.codecogs.com/gif.latex?n)����ͬ��С��Բ�̣�Ҫ����������һ��һ���ƶ�������B�ϣ�����ÿ���ƶ�ͬһ�������϶����ܳ��ִ�������С�����Ϸ�������������Ҫ���ٴ��ƶ���

>����

>Բ�̸���![](http://latex.codecogs.com/gif.latex?n)��

>���

>��ŵ���ƶ�����

ʾ�����룺

```C++
#include<cstdio>
using namespace std;
void hanoi(int x,int A,int B){
//x��ʾ��ʣԲ������ ,A��ʾ�����Ӵ��ĸ�λ�ã��������Ǽ���Ϊpλ�ã���B��ʾ�Ƶ��ĸ�λ�ã��������Ǽ���Ϊqλ�ã���
    if (!x) return;
    //���x==0����û��Բ����Ҫ�ƶ�ʱ������������������
    hanoi(x-1,A,3-A-B);
    //��p��n-1��Բ���ƶ�����p��q������Ǹ�λ�ã����Ǽ����λ��Ϊm��
    printf("%d:%c->%c\n",x,'A'+A,'A'+B);
    //��p�ϵ�n-1��Բ�̾��ƶ�����m(��һ����ɺ�)������ѵ�ǰp�Ͻ�����Ǹ�Բ���ƶ���q�Ĳ���
    hanoi(x-1,3-A-B,B);
    //��m��n-1�������ƶ���q
    //��n=1ʱ�������ݹ���䶼����ִ����Ч���ݣ����������������һ��Բ�̴�p�ƶ���q�Ĳ���
}
int main() {
    int n;
    scanf("%d",&n);
    hanoi(n,0,1);
    //����0 1�����A�Ƶ�B��'A'+0='A','A'+1='B'
}
```
��ŵ������ĵݹ�ⷨ���ǽ���A��![](http://latex.codecogs.com/gif.latex?n)��Բ���ƶ���B�����⻯Ϊ��A��![](http://latex.codecogs.com/gif.latex?n-1)��Բ���ƶ���C���ٰ�A������Բ���ƶ���B������C��![](http://latex.codecogs.com/gif.latex?n-1)��Բ���ƶ���B�����⡣

���ں�ŵ���������Žⲽ�����ǻ�����ͨ���·�����ѧ��ѧ��ʽ��

![](http://latex.codecogs.com/gif.latex?a[n]~=~2*a[n-1]+1)

![](http://latex.codecogs.com/gif.latex?a[1]~=~1)

![](http://latex.codecogs.com/gif.latex?a[n]~=~2^n~-~1)

