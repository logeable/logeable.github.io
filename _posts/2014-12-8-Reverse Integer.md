---
layout: post
title: Reverse Integer
category: [leetcode,algorithm]
---

Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321

[https://oj.leetcode.com/problems/reverse-integer/](https://oj.leetcode.com/problems/reverse-integer/) 

<!--break-->

---

这里要注意判断翻转后的值会不会超过int范围。
```
hints:
1234%10==4
-1234%10==-4
```
```c++
int reverse(int x)
{
	int max=numeric_limits<int>::max();
	int min=numeric_limits<int>::min();

	int result=0;
	while(x!=0)
	{
		if(result<min/10||result>max/10)
		{
			return 0;
		}
		result=result*10+x%10;
		x/=10;
	}
	return result;
}
```
