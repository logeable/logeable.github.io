---
layout: post
title: Count and Say
category: [leetcode,algorithm]
---
The count-and-say sequence is the sequence of integers beginning as follows:
1, 11, 21, 1211, 111221, ...

1 is read off as *"one 1"* or 11. 
11 is read off as *"two 1s"* or 21. 
21 is read off as *"one 2, then one 1"* or 1211.  

Given an integer n, generate the nth sequence.

Note: The sequence of integers will be represented as a string.
Given a roman numeral, convert it to an integer.


[https://oj.leetcode.com/problems/count-and-say/](https://oj.leetcode.com/problems/count-and-say/) 

<!--break-->

---

```c++

#include <iostream>
#include <string>
#include <sstream>
using namespace std;

class Solution
{
public:
	string countAndSay(int n)
	{
		string str{"1"};
		if(n==1)
		{
			return str;
		}
		for(int i=1;i<n;i++)
		{
			str=generate(str);
			
		}
		return str;
	}
	string generate(string str)
	{
		ostringstream oss;
		if(str.length()==1)
		{
			oss<<1<<str[0];
			return oss.str();
		}
		int len=1;
		for(size_t i=1;i<str.length();i++)
		{
			if(str[i]!=str[i-1])
			{
				oss<<len<<str[i-1];
				len=1;
				if(i==str.length()-1)
				{
					oss<<1<<str[i];
				}
			}
			else
			{
				len++;
				if(i==str.length()-1)
				{
					oss<<len<<str[i];
				}
			}
		}
		return oss.str();
	}
};

int main(int argc,char*argv[])
{
	cout<<Solution().countAndSay(6)<<endl;
	return 0;
}

```
