---
layout: post
title: Palindrome Number
category: [leetcode,algorithm]
---

Determine whether an integer is a palindrome. Do this without extra space.

Some hints:
Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.

[https://oj.leetcode.com/problems/palindrome-number/](https://oj.leetcode.com/problems/palindrome-number/) 

<!--break-->

---

要注意负数不会是回文的。
ps:介绍中提到:

However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow


但是还是ac的。

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
bool isPalindrome(int x)
{
	return x>=0&&x==reverse(x);
}
```
