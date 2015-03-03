---
layout: post
title: Roman to Integer
category: [leetcode,algorithm]
---
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

[https://oj.leetcode.com/problems/roman-to-integer/](https://oj.leetcode.com/problems/roman-to-integer/) 

<!--break-->

---


```c++

#include <iostream>
#include <string>
#include <map>
using namespace std;

class Solution 
{
public:
	Solution()
	{
		mci['I']=1;
		mci['V']=5;
		mci['X']=10;
		mci['L']=50;
		mci['C']=100;
		mci['D']=500;
		mci['M']=1000;
	}
    int romanToInt(string s) 
	{
		int num=0;
		for(size_t i=0;i<s.length();i++)
		{
			if(i>0)
			{
				if(mci[s[i-1]]<mci[s[i]])
				{
					num=num+mci[s[i]]-2*mci[s[i-1]];
				}
				else
				{
					num+=mci[s[i]];
				}
			}
			else
			{
				num+=mci[s[i]];
			}
		}
		return num;
	}
private:
	map<char,int> mci;
};

int main(int argc,char*argv[])
{
	Solution s;
	cout<<s.romanToInt("DCXXI")<<endl;
	return 0;
}

```
[http://zh.wikipedia.org/wiki/罗马数字](http://zh.wikipedia.org/wiki/罗马数字)
