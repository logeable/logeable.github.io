---
layout: post
title: 不使用乘除法或if while for 求1...n的和
category: [algorithm]
---

在知乎上的一道题，记录下来。

<!--break-->

---

```c++
#include <iostream>
using namespace std;

int sum(int n)
{
	static decltype(&sum) fun[]={[](int){return 0;},sum};
	return n+fun[n>0](n-1);
}

class Sum
{
public:
	Sum()
	{
		cur++;
		sum+=cur;
	}
	static int sum;
	static int cur;
};
int Sum::sum=0;
int Sum::cur=0;

int main(int argc,char *argv[])
{
	cout<<sum(10)<<endl;
	Sum s[10];
	cout<<Sum::sum<<endl;
	return 0;
}
```
