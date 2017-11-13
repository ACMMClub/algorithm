# ACMM协会第三周讲座总结 

---

## 排序

### 降序和升序排列

### 选择排序

- 依次寻最小（大）值，进行![](http://latex.codecogs.com/gif.latex?n-1)次寻找得到有序数列。

- 复杂度 ![](http://latex.codecogs.com/gif.latex?O(n^{2}))

- 升序排列的选择排序代码示例如下:

```C++

void swap(int &a,int &b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
}

void choose_sort(int arr[],int num)
{
    //num代表数列元素个数
    for (int m = 0; m < num; m++)
		for (int n = m + 1; n < num; n++)
			if (arr[m] > arr[n])swap(arr[m], arr[n]);
}

```

### 冒泡排序

- 从![](http://latex.codecogs.com/gif.latex?i=0)开始每次比较两个相邻的元素![](http://latex.codecogs.com/gif.latex?a[i])与![](http://latex.codecogs.com/gif.latex?a[i+1])，较为大（小）的元素向上冒泡（传递），![](http://latex.codecogs.com/gif.latex?i++)。重复进行上述比较![](http://latex.codecogs.com/gif.latex?n-1)次。

- 复杂度 ![](http://latex.codecogs.com/gif.latex?O(n^{2}))

```C++

void swap(int &a,int &b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
}

void bubble_sort(int arr[], int num)
{
	for(int m = 0; m < num ;m++ )
		for (int n = 0 ; n < num - m - 1; n++)
			if (arr[n] > arr[n+1])swap(arr[n], arr[n+1]);
}

```

### 插入排序

- 依次把数组中的元素插入一个已排序的数组，得到的数组也是排序的。将数列中各个元素依次插入一个空序列。

- 复杂度 最优：![](http://latex.codecogs.com/gif.latex?O(n)) 最劣：![](http://latex.codecogs.com/gif.latex?O(n^{2}))

- 在C++中，插入排序主要用于链表，因为无论是数组还是非链表型容器，“插入”往往意味着大量的移位操作

### 归并排序

- 采用分治法,先使每个子序列有序，再使子序列段间有序，将已有序的子序列合并，得到完全有序的序列。

- 复杂度 ![](http://latex.codecogs.com/gif.latex?O(%20n%20\\log%20{n}))

```C++

void swap(int &a,int &b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
}

void merge(int *data,int start,int end,int *result)
 {
     int left_length = (end - start + 1) / 2 + 1;
     //左部分区间的数据元素的个数
     int left_index = start;
     int right_index = start + left_length;
     int result_index = start;
     while(left_index < start + left_length && right_index < end+1)
     {
         //对分别已经排好序的左区间和右区间进行合并
         if(data[left_index] <= data[right_index])
             result[result_index++] = data[left_index++];
         else
             result[result_index++] = data[right_index++];
     }
     while(left_index < start + left_length)
         result[result_index++] = data[left_index++];
     while(right_index < end+1)
         result[result_index++] = data[right_index++];
 }

void merge_sort(int *data, int start, int end, int *result)
 {
     if(1 == end - start)//如果区间中只有两个元素，则对这两个元素进行排序
     {
         if(data[start] > data[end])
         {
             swap(data[start],data[end]);
         }
        return;
    }
     else if(0 == end - start)//如果只有一个元素，则不用排序
         return;
     else
     {
         //继续划分子区间，分别对左右子区间进行排序
         merge_sort(data,start,(end-start+1)/2+start,result);
         merge_sort(data,(end-start+1)/2+start+1,end,result);
         //开始归并已经排好序的start到end之间的数据
         merge(data,start,end,result);
         //把排序后的区间数据复制到原始数据中去
         for(int i = start;i <= end;++i)
             data[i] = result[i];
     }
 }

```

### 快速排序

- 通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列。

- 复杂度 ![](http://latex.codecogs.com/gif.latex?O(n%20\\log%20{n}))

```C++

void quick_sort(int s[], int l, int r)  
{  
    if (l< r)  
    {        
        int i = l, j = r, x = s[l];  
        while (i < j)  
        {  
            while(i < j && s[j]>= x) 
            // 从右向左找第一个小于x的数  
                j--;   
            if(i < j)  
                s[i++] = s[j];  
            while(i < j && s[i]< x) 
            // 从左向右找第一个大于等于x的数  
                i++;   
            if(i < j)  
                s[j--] = s[i];  
        }  
        s[i] = x;  
        quick_sort(s, l, i - 1); 
        // 递归调用  
        quick_sort(s, i + 1, r);  
    }  
}  

```

### 基数排序

- 该排序不基于比较，消耗巨大空间的代价换取时间的优势

- 透过键值的部份资讯，将要排序的元素分配至某些“桶”中，藉以达到排序的作用

- 复杂度 ![](http://latex.codecogs.com/gif.latex?O(n*m)) ,![](http://latex.codecogs.com/gif.latex?m)为位数

## 贪心算法

### 背包问题

- 不同的物品价值相同,一共有![](http://latex.codecogs.com/gif.latex?n)个物品，第![](http://latex.codecogs.com/gif.latex?i)个物品大小为![](http://latex.codecogs.com/gif.latex?s[i])，背包总容量为![](http://latex.codecogs.com/gif.latex?C)，求背包能容纳的最多物品数

- 排序![](http://latex.codecogs.com/gif.latex?n)个物品，每次拿大小最小的物品（即取局部最优解），直到无法装下

代码示例：

```C++

int bag_problem(int n, int C, int s[])
{
	std::sort(s, s + n);
	int num = 0;
	while ((C -= s[num]) >= 0 && num < n)num++;
	return num;
}

```

### 背包问题 **plus**

- 不同物品价值不相同，物品可以切割,一共有![](http://latex.codecogs.com/gif.latex?n)个物品，第![](http://latex.codecogs.com/gif.latex?i)个物品大小为![](http://latex.codecogs.com/gif.latex?s[i])，价值为![](http://latex.codecogs.com/gif.latex?v[i]),背包总容量为![](http://latex.codecogs.com/gif.latex?C)，求背包能容纳的最多物品数

- 用物品单位价值排序![](http://latex.codecogs.com/gif.latex?n)个物品，每次拿单位价值最高的物品（即取局部最优解），直到无法装下

代码示例：

```C++

double bag_problem_plus(int n, int C, int s[], int v[], double s_v[])
{
	//s_v用于存储单位价值
	std::map<double, int> things;
	for (int num = 0; num < n; num++)
	{
		s_v[num] = v[num] /1.0/ s[num];
		if (things[s_v[num]])things[s_v[num]] += s[num];
		else things[s_v[num]] = s[num];
	}
	std::sort(s_v,s_v+n);
	int pos = n - 1;
	double value = 0;
	while ((C - things[s_v[pos]]) > 0 && pos >= 0)
	{
		C -= things[s_v[pos]];
		value += things[s_v[pos]]*s_v[pos];
		pos--;
		while (s_v[pos] == s_v[pos + 1])pos--;
	}
	if(pos >= 0)value += C * s_v[pos];
	return value;
}

```

### 乘船问题

- ![](http://latex.codecogs.com/gif.latex?n)个人要过河，体重分别为![](http://latex.codecogs.com/gif.latex?w[n]),船载重为![](http://latex.codecogs.com/gif.latex?G)(船最多只能载两个人)，问船最少来回运送几次

- 按照体重大小排序，由最轻的开始，其与可以和他一起坐船的人中最重的一起坐（若无则自己一个人坐），直到所有人都到对岸

代码示例:

```C++

int search_index(int w[], int start , int end, int num)
{
	//返回有序数列w中小于等于num的最大数的index,且index属于(start,end]
	for (int m = end; m > start; m--)
	{
		if (w[m] <= num)return m;
	}
	//若不存在则返回0
	return 0;
}

int boat_problem(int w[], int n,int G)
{
	std::sort(w, w + n);
	int num = 0;
	int start = 0;
	int end = n - 1;
	while (start < n)
	{
		if (end = search_index(w, start, end, G-w[start]))
		{
			end--;
			start++;
			num++;
		}
		else
		{
			return n - num;
		}
	}
	return num;
}


```

### 区间选择问题

- 数轴上![](http://latex.codecogs.com/gif.latex?n)个闭区间，第![](http://latex.codecogs.com/gif.latex?i)个区间为![](http://latex.codecogs.com/gif.latex?[a[i],b[i]]),问最多选取多少个区间使选取的区间互不相交

- 思路：确认![](http://latex.codecogs.com/gif.latex?[a[0]，b[0]])(![](http://latex.codecogs.com/gif.latex?n)个闭区间以![](http://latex.codecogs.com/gif.latex?a[i])从小到大排序),寻找![](http://latex.codecogs.com/gif.latex?b[m]<b[0])，![](http://latex.codecogs.com/gif.latex?m>0)，若找到了符合要求的![](http://latex.codecogs.com/gif.latex?b[m])则删去![](http://latex.codecogs.com/gif.latex?n\\in%20[0,m))的闭区间，使用![](http://latex.codecogs.com/gif.latex?[a[m],b[m]])重复进行该操作；

- 若找不到符合要求的元素，则区间![](http://latex.codecogs.com/gif.latex?[a[i]，b[i]])必定在最优解内，用![](http://latex.codecogs.com/gif.latex?[a[t],b[t]])重复进行该操作（![](http://latex.codecogs.com/gif.latex?a[t]>b[i]),![](http://latex.codecogs.com/gif.latex?t)为满足前式且大于![](http://latex.codecogs.com/gif.latex?i)的最小数）

代码示例：

```C++

struct Section
{
	int left;
	int right;
	Section(int x,int y)
	{
		left = x;
		right = y;
	}
};
int section_problem(std::vector<Section> s)
{
	//这里假设s按照s.left从小到大已排好序，即排序过程略
	int sum = 0;
	int pos = 0;
	while (pos < s.size())
	{
		bool is_it_change = 0;
		for (int num = pos + 1; num < s.size(); num++)
		{
			if (s[num].right < s[pos].right)
			{
				pos = num;
				is_it_change = 1;
				break;
			} 
		}
		if (is_it_change)continue;
		sum++;
		for (int num = pos + 1; num < s.size(); num++)
		{
			if (s[num].left > s[pos].right)
			{
				pos = num;
				is_it_change = 1;
				break;
			}
		}
		if (!is_it_change)break;
	}
	return sum;
}

```

### 区间选择问题 **plus**

- 数轴上![](http://latex.codecogs.com/gif.latex?n)个闭区间，第i个区间为![](http://latex.codecogs.com/gif.latex?[a[i],b[i]]),问最少选取多少个区间使选取的区间的并集覆盖![](http://latex.codecogs.com/gif.latex?[A,B])

- 思路：选择![](http://latex.codecogs.com/gif.latex?a[m]\\leqslant%20A)中，![](http://latex.codecogs.com/gif.latex?b[m])最大的区间，把![](http://latex.codecogs.com/gif.latex?b[m])当做![](http://latex.codecogs.com/gif.latex?A)，重新进行上次操作

代码示例：

```C++

struct Section
{
	int left;
	int right;
	Section(int x,int y)
	{
		left = x;
		right = y;
	}
};
int section_problem_iterator(std::vector<Section> s,int A,int B,int pos)
{
	//这里假设s按照s.left从小到大已排好序，即排序过程略
	if (A >= B)return 0;
	for (int m = pos + 1; m < s.size(); m++)
	{
		if (s[m].left <= A)
		{
			if (s[m].right > s[pos].right)pos = m;
		}
		else return 1 + section_problem_iterator(s,s[pos].right ,B , pos);
	}
	return 1 + section_problem_iterator(s, s[pos].right, B, pos);
}
int section_problem_plus(std::vector<Section> s, int A, int B)
{
	//这里需保证满足题目要求的情况必定存在，否则会陷入死循环；我们可以传递一个参数来增加若无满足题目要求的情况存在的判定
	if (A >= B)return 0;
	if (s.size() == 0)return 0;
	return section_problem_iterator(s, A, B, 0);
}

```

### 区间选择问题 **plus** **plus**

- 数轴上![](http://latex.codecogs.com/gif.latex?n)个闭区间，第![](http://latex.codecogs.com/gif.latex?i)个区间为![](http://latex.codecogs.com/gif.latex?[a[i],b[i]]),问最多选取多少个区间使选取的数轴上的每一个位置至多被![](http://latex.codecogs.com/gif.latex?k)个区间所覆盖

- 思路：区间选择问题就等于这个问题的![](http://latex.codecogs.com/gif.latex?k=1)的情况。

- 既然k是一个变量，那我们可以维护一个大小为![](http://latex.codecogs.com/gif.latex?k)的表格，若当前表格项目数小于![](http://latex.codecogs.com/gif.latex?k)，则把下一个元素加入，若当前表格项目数等于![](http://latex.codecogs.com/gif.latex?k)，则把表格中![](http://latex.codecogs.com/gif.latex?b[i])最大的元素取出进行与区间选择问题类似的操作。

- 取得最优解后，将![](http://latex.codecogs.com/gif.latex?a[i])最小的元素弹出，再进行下一轮维护。

### 国王游戏

- 恰逢 H 国国庆，国王邀请 ![](http://latex.codecogs.com/gif.latex?n) 位大臣来玩一个有奖游戏。首先，他让每个大臣在左、右手上面分别写下一个整数，国王自己也在左、右手上各写一个整数。

- 然后，让这 ![](http://latex.codecogs.com/gif.latex?n) 位大臣排成一排，国王站在队伍的最前面。

- 排好队后，所有的大臣都会获得国王奖赏的若干金币，每位大臣获得的金币数分别是：排在该大臣前面的所有人的左手上的数的乘积除以他自己右手上的数，然后向下取整得到的结果。

- 国王不希望某一个大臣获得特别多的奖赏，所以他想请你帮他重新安排一下队伍的顺序，使得获得奖赏最多的大臣，所获奖赏尽可能的少。注意，国王的位置始终在队伍的最前面。



- 思路：相邻两个的人交换对于前面的人答案没影响，而且对于后面的人答案也没有影响。也就是说相邻两人的位置交换只会对这两个人产生影响。那么我们就先考虑这两个人。
        设这两个人分别为![](http://latex.codecogs.com/gif.latex?i)和![](http://latex.codecogs.com/gif.latex?i+1)。左手数字为![](http://latex.codecogs.com/gif.latex?a[i])和![](http://latex.codecogs.com/gif.latex?a[i+1])，右手数字为![](http://latex.codecogs.com/gif.latex?b[i])和![](http://latex.codecogs.com/gif.latex?b[i+1])。两人的金币数为![](http://latex.codecogs.com/gif.latex?w[i])和![](http://latex.codecogs.com/gif.latex?w[i+1])。
        记![](http://latex.codecogs.com/gif.latex?P[i]=a[1]*a[2]*a[3]*...*a[i])
        可得：
            ![](http://latex.codecogs.com/gif.latex?w[i]=P[i-1]/b[i];)
            ![](http://latex.codecogs.com/gif.latex?w[i+1]=P[i]/b[i+1];)
        又![](http://latex.codecogs.com/gif.latex?P[i]=P[i-1]*a[i])
        那么 ![](http://latex.codecogs.com/gif.latex?w[i+1]=P[i-1]*a[i]/b[i+1]=w[i]*a[i]*b[i]/b[i+1])
    不难看出，在这个相邻的二元组中，前面的数不受后面的影响，而后面的金币数决定于![](http://latex.codecogs.com/gif.latex?w[i]),![](http://latex.codecogs.com/gif.latex?a[i]),![](http://latex.codecogs.com/gif.latex?b[i])。
    推广到整个排队方案，前面的金币数和![](http://latex.codecogs.com/gif.latex?a[i]),![](http://latex.codecogs.com/gif.latex?b[i])都会影响后面的答案。贪心原则便出来了：按![](http://latex.codecogs.com/gif.latex?a[i]*b[i])为关键字从小到大排序，相同的顺序无所谓。最后再扫一遍，算出答案即可。

代码示例:

```C++

#include<cstdio>  
#include<cstdlib>  
#include<cstring>  
#include<cmath>  
#include<ctime>  
#include<iostream>  
#include<algorithm>  
using namespace std;  
int N;  
int a[1005],b[1005],ka,kb;  
int ans[20000],t[20000],lena,lent,tt[20000],t2[20000],len;  
void _qst_ab(int l,int r)  
{  
    int i=l,j=r,ma=a[(i+j)>>1],mb=b[(i+j)>>1];  
    while(i<=j)  
    {  
        while(a[i]*b[i]<ma*mb) i++;  
        while(a[j]*b[j]>ma*mb) j--;  
        if(i<=j)  
        {  
            swap(a[i],a[j]);  
            swap(b[i],b[j]);  
            i++;j--;  
        }  
    }  
    if(l<j) _qst_ab(l,j);  
    if(i<r) _qst_ab(i,r);  
}  
void _init()  
{  
    scanf("%d%d%d",&N,&a[0],&b[0]);  
    for(int i=1;i<=N;i++)  
        scanf("%d%d",&a[i],&b[i]);  
}  
void _get_t(int Left,int Right)  
{  
    for(int i=1;i<=lent;i++)  
    {  
        tt[i]+=t[i]*Left;  
        tt[i+1]+=tt[i]/10;  
        tt[i]%=10;  
    }  
    lent++;  
    while(tt[lent]>=10)  
    {  
        tt[lent+1]=tt[lent]/10;  
        tt[lent]%=10;  
        lent++;  
    }  
    while(lent>1&&tt[lent]==0) lent--;  
    len=lent;  
    memcpy(t,tt,sizeof(tt));  
    memset(tt,0,sizeof(tt));  
    for(int i=1,j=len;i<=len;i++,j--)  
        t2[i]=t[j];  
    int x=0,y=0;  
    for(int i=1;i<=len;i++)  
    {  
        y=x*10+t2[i];  
        tt[i]=y/Right;  
        x=y%Right;  
    }  
    x=1;  
    while(x<len&&tt[x]==0) x++;  
    memset(t2,0,sizeof(t2));  
    for(int i=1,j=x;j<=len;i++,j++)  
        t2[i]=tt[j];  
    memcpy(tt,t2,sizeof(t2));  
    len=len+1-x;  
}  
bool _cmp()  
{  
    if(len>lena) return true;  
    if(len<lena) return false;  
    for(int i=1;i<=len;i++)  
    {  
        if(ans[i]<tt[i]) return true;  
        if(ans[i]>tt[i]) return false;  
    }  
    return false;  
}   
void _solve()  
{  
    _qst_ab(1,N);  
    t[1]=1;lent=1;  
    for(int i=1;i<=N;i++)  
    {  
        memset(tt,0,sizeof(tt));  
        len=0;  
        _get_t(a[i-1],b[i]);  
        if(_cmp())  
        {  
            memcpy(ans,tt,sizeof(tt));  
            lena=len;  
        }  
    }  
    for(int i=1;i<=lena;i++)  
        printf("%d",ans[i]);  
    printf("\n");  
}  
int main()  
{  
    _init();  
    _solve();  
    return 0;  
}  

```

