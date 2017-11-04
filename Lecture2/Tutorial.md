# 2017ACMM算法讲堂第二周：字符串处理 题解

### 作者：关东阳


- [A - Free Cash](#A)
- [B - Hulk](#B)
- [C - Simple prefix compression](#C)
- [D - Fraction](#D)
- [E - Search for Pretty Integers](#E)
- [F - Borya's Diagnosis](#F)
- [G - Game With Sticks](#G)
- [H - Vertical Histogram](#H)


## 总述
本套题目主要是一些模拟题和字符串处理，适合零基础的同学进行入门。  
为了让大家熟悉字符串数组char[]与字符串类string，前五题使用字符串数组char[]，后五题使用字符串类string。  
同时本套题目中多次出现需要用 now 与 pre 比较的题目，一般可以采取两种做法：  
一是每读入一个新的 now 之前，把 pre 给替换成 now。下列程序采用的都是这种做法。  
二是利用读入次数 K 的奇偶判断，若K为奇数，读入A1，与A2比较；若K为偶数，读入A2，与A1比较。有兴趣的同学可以去尝试下。  
详细题解见下。

##A - Free Cash <div id="A"></div>
### 题目描述
给定一系列时间hi,mi,求出最多有多少个时间相同。

### Solution
用th,tm表示前一个时间，h,m表示当前时间，进行比对，看是否相同，
若相同则计数加一，否则计数重置。

### 知识点
模拟

### 代码
```c++
#include <cstdio>

int main()
{
	int n,h,m,th,tm,min=1,temp=1;
	scanf("%d",&n);
	scanf("%d%d",&th,&tm);
	n--;
	while (n--)
	{
		scanf("%d%d",&h,&m);
		if (h==th && m==tm)
			temp++;
		else
			temp=1;
				
		th=h;
		tm=m;
		if (min<temp)
			min=temp;
	}
	printf("%d",min);
	return 0;
} 
```


## B - Hulk <div id="B"></div>
### 题目描述
给定 n ,根据规律输出  
I hate it，  
I hate that I love it，  
I hate that I love that I hate it 等等。

### Solution
可以看出 n 每次 +1，都是在前一句 n-1 的 “……it” 前面添加 “that I   love” 或者 “that I hate” （n为偶数输出前句，n为奇数输出后句）。  
即添加的位置为“I hate …(that I love) it”,括号内为添加内容。

### 知识点
模拟

### 代码

```c++
#include <cstdio> 

int main()
{
	int n;
	scanf("%d",&n);
	printf("I hate");
	for (int i=1;i<n;i++)
	{
		printf(" that I ");
		if (i%2==0)
			printf("hate");
		else
			printf("love");
	}
	printf(" it\n");
	return 0;
} 
```


## C - Simple prefix compression<div id="C"></div>
### 题目描述
设上一个字符串为a,当前的字符串b,若b从0处开始与a存在连续的公共部分，则该部分可用单个字符替换。  
统计所有字符串的总长度。  
如样例 


> abc  
atest  
atext

可改写成
> abc  
1test  
3xt

### Solution
每次对b与a从头开始比对，取k=strlen(b)，则每有一个位置的a[j]=b[j]，k减一，直到a[j]!=b[j],把k加到sum里面。

### 知识点
模拟

### 代码
```c++
#include <cstdio>
#include <cstring>
using namespace std;

int main()
{
	int n,sum,l1,l2,l;
	char a[260],b[260];
	scanf("%d",&n);
	scanf("%s",a);
	l1=strlen(a);
	sum=l1;
	
	for (int i=1;i<n;i++)
	{
		scanf("%s",b);
		int l2=strlen(b);
		int j,k=l2;
		l=l1<l2?l1:l2;
		for (j=0;j<l;j++)
			if (a[j]==b[j])
				k--;
			else
				break;
		sum=sum+k+1;
		l1=l2;
		strcpy(a,b);
	}
	
	printf("%d",sum);
	return 0; 
} 
```

## D - Fraction<div id="D"></div>
### 题目描述
把n拆成两个互质的数a,b之和，同时要让 a / b < 1的前提下尽可能大。

### Solution
那从 i = n / 2 开始枚举，这样最先枚举出来互质的 n 和 n - i 一定能保证 （ n / n - i ）< 1 并且最大。

### 知识点
数学

### 代码
```c++
#include <cstdio>

int gcd(int a,int b)
{
	return b?gcd(b,a%b):a;
}

int main()
{
	int n;
	scanf("%d",&n);
	for (int i=n/2;i>=1;i--)
		if (gcd(i,n-i)==1)
		{
			printf("%d %d",i,n-i);
			break;
		}
	return 0;
}
```

## E - Search for Pretty Integers<div id="E"></div>
### 题目描述
给定两个数组，要你求出一个数K，它各位的数字要在这两个数组中的某一个至少出现过一次，并且要让K尽可能小。  
  
如样例输入：
>  
4 2  
5 7 6

样例输入：

>25  

其中25中的2在前一数组中出现了，5则在后一数组中出现过。


### Solution

两种方法；  

一是用两个哈希数组hash_a,hash_b记录ai,bj分别出现次数，  
因为 1 <= ai,bj <=9，所以若有一个数同时在两个数组中出现（即在两个哈希数组中出现次数都大于 1），  
它一定比两个组合来的数要小，若没有，则取两个数组中各自最小的数进行组合。
  
二是用排序，把所有数据分别读入a,b数组中，直接取数组头元素比较输出。  

一方法速度更快，二方法代码更简单。
### 知识点
哈希，排序

### 代码
```c++
#include <cstdio>

int a[11],b[11],x,n,m;
int mina=100,minb=100;

int main()
{
	scanf("%d%d",&n,&m);
	for (int i=0;i<n;i++)
	{
		scanf("%d",&x);
		a[x]++;
		if (mina>x)
			mina=x;
	}
	
	for (int i=0;i<m;i++)
	{
		scanf("%d",&x);
		b[x]++;
		if (minb>x)
			minb=x;
	}
	
	for (int i=1;i<10;i++)
		if (a[i]&&b[i])
		{ 
			printf("%d",i);
			return 0; 
		}
	
	if (mina<minb)
		printf("%d",mina*10+minb);
	else
		printf("%d",minb*10+mina);
	return 0;
}
```

## F - Borya's Diagnosis<div id="F"></div>
### 题目描述
Borya需要按给定顺序看医生，每个医生有不同的出诊日期（出诊日期为 s , s+d , s+2*d , …）。  
求看完最后一个医生的日期。

### Solution
因为要按顺序见医生，所以对每一个要见的医生，ans一定要能大于他某一个出诊日期并且Borya要能够去看。  
每次更新ans即可。

### 知识点
模拟

### 代码
```c++
#include <cstdio>

int main()
{
	int n,s,d,ans=0;
	scanf("%d",&n);
	while (n--)
	{
		scanf("%d%d",&s,&d); 
		if (ans<s)
			ans=s;
		else
		{
			while (s<=ans)
				s+=d;
			ans=s;
		}
	}
	printf("%d",ans);
	return 0;
}
```

## G - Game With Sticks<div id="G"></div>
### 题目描述
给定一个由纵向n，以及横向m根木棍，搭成的图。木棍交错形成了n*m个点。  
两人轮流取一个点，把该点上的两根木棍移开。  
当无点可取即输掉游戏，问谁能赢得比赛。

### Solution
两种方法：  

一是模拟：模拟下会发现其实选择任意一个点去除两根木棍，剩下的结果都是一样的，这就给了我们模拟的思路。
  
二是数学：假设当前剩下的纵向和横向木棍数目为 n，m ，剩余的点数目为 n * m ，  每次选择一个点去除木棍，  
那么跟着去掉的点的数目为（ n + m - 1),所以剩下了 n * m - n - m + 1，即（n - 1）*（m - 1),  
若（n - 1）或（m - 1)等于0则停止，判断胜负。  
所以我们只要对min(n,m)判断奇偶即可，奇数则Akshat赢，偶数则Malvika赢。

### 知识点
模拟，数学

### 代码
```c++
#include <cstdio>

int main()
{
	int n,m;
	scanf("%d%d",&n,&m);
	if (n>m)
		n=m;
	if (n%2==1)
		printf("Akshat");
	else
		printf("Malvika");
	return 0;
}
```

## H - Vertical Histogram<div id="H"></div>
### 题目描述
给定四行字符串，统计每个大写字母出现的次数，按给定格式输出。  
出现几次，则 ' * ' 有多少个。

### Solution
读取一行可使用getline(cin,str)。  
开一个num[]数组记录26个大写字母出现的次数，用maxl表示最大出现次数，则maxl为输出图形的高。

### 知识点：
字符串，模拟

### 代码
```c++
#include <iostream>
#include <cstdio>
#include <string>
#include <cctype>
using namespace std;

string s;
int num[27],maxl;

int main()
{
	for (int i=0;i<4;i++)
	{
		getline(cin,s);
		for (int j=0;j<s.length();j++)
			if (isupper(s[j]))
			{
				num[s[j]-'A']++;
				if (num[s[j]-'A']>maxl)
					maxl=num[s[j]-'A'];
			}
	}
	
	for (int i=0;i<maxl;i++)
	{
		for (int j=0;j<26;j++)
			if (num[j]>=maxl-i)
				printf("* ");
			else
				printf("  ");
		printf("\n");
	}
	
	for (int i=0;i<26;i++)
		printf("%c ",i+'A');
	printf("\n");
	return 0;
} 
```

## I - I Wanna Be the Guy<div id="I"></div>
### 题目描述
小明小红一起玩 “ I Wanna Be the Guy ” 游戏，  
但他们能通过的关卡各不相同。  
其中小明能通过a1,a2,…，关，小红能通过b1,b2,…，关。  
问他们合作能否通过所有关卡。

### Solution
开个哈希数组hash[]，若i关卡能被小明或小红通过，则设为1，若i关卡无法被其中任意一个人通过，设为0。  
若所有关卡的hash[]都为1，则说明该游戏能被他们双人合作通关。

### 知识点
哈希

### 代码
```c++
#include <cstdio>
bool hash[105];
int n,k,x;

int main()
{
	scanf("%d%d",&n,&k);
	for (int i=0;i<k;i++)
	{
		scanf("%d",&x);
		hash[x]=1;
	}
	
	scanf("%d",&k);
	for (int i=0;i<k;i++)
	{
		scanf("%d",&x);
		hash[x]=1;
	}
	
	for (int i=1;i<=n;i++)
		if (!hash[i])
		{
			printf("Oh, my keyboard!\n");
			return 0;
		}
	printf("I become the guy.\n");
	return 0;
}
```

## J - 字符串替换<div id="J"></div>
### 题目描述
编写一个C程序实现将字符串中的所有"you"替换成"we"。  
输入数据按行输入。

### Solution
用 getline() 按行读入字符串。  
用 pos 标记当前位置，用 string 类中的 find() 和 replace() 完成查找和替换。

### 知识点
字符串

### 代码

```c++
#include <iostream>
#include <string>
using namespace std;

int main()
{
	string s;
	while (getline(cin,s))
	{
		int pos=0;
		while ( (pos=s.find("you",pos))!=string::npos)
			s.replace(pos++,3,"we");    
		cout<<s<<endl;      
	}
	return 0;
}
```


