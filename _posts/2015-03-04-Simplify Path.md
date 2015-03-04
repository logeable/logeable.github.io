---
layout: post
title: Simplify Path
category: [leetcode,algorithm]
---
Given an absolute path for a file (Unix-style), simplify it.

For example, 
path = "/home/", => "/home" 
path = "/a/./b/../../c/", => "/c" 

Corner Cases: 
Did you consider the case where path = "/../"? 
In this case, you should return "/". 
Another corner case is the path might contain multiple slashes '/' together, such as "/home//foo/". 
In this case, you should ignore redundant slashes and return "/home/foo". 

[https://oj.leetcode.com/problems/simplify-path/](https://oj.leetcode.com/problems/simplify-path/) 

<!--break-->

---



```c++

#include <iostream>
#include <string>
#include <vector>
#include <iterator>
#include <algorithm>
#include <sstream>
#include <stack>
using namespace std;

class Solution
{
public:
	string simplifyPath(string path)
	{
		vector<string> vs=split(path,"/");
		vector<string> s;
		for(auto str:vs)
		{
			if(str==".")
			{
				continue;
			}
			else if(str=="..")
			{
				if(s.empty())
				{
					continue;
				}
				s.pop_back();
			}
			else
			{
				s.push_back(str);
			}
		}
		ostringstream oss;
		for(auto str:s)
		{
			oss<<"/"<<str;
		}
		if(s.empty())
		{
			oss<<"/";
		}
		return oss.str();
	}

	vector<string> split(string str,string delim)
	{
		vector<string> vs;
		size_t pos;
		while((pos=str.find(delim))!=string::npos)
		{
			auto token=str.substr(0,pos);
			if(!token.empty())
			{
				vs.push_back(token);
			}
			str.erase(0,pos+delim.length());
		}
		if(!str.empty())
		{
			vs.push_back(str);
		}
		return vs;
	}
};

int main(int argc,char*argv[])
{
	Solution s;
	cout<<s.simplifyPath(argv[1])<<endl;
	return 0;
}

```
