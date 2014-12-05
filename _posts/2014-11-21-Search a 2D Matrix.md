---
layout: post
title: Search a 2D Matrix
category: [leetcode,algorithm]
---

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

For example,
Consider the following matrix:
```
[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
```
[https://oj.leetcode.com/problems/search-a-2d-matrix/](https://oj.leetcode.com/problems/search-a-2d-matrix/) 

<!--break-->

---
####本题采用二分搜索。
```c++
class Solution
{
public:
	bool searchMatrix(vector<vector<int>> &matrix,int target)
	{
		int l,r,mid;
		l=0;
		r=matrix.size()-1;
		while(l<=r)
		{
			mid=l+(r-l)/2;
			int flag=false;
			for(auto m:matrix[mid])//判断target是否在当前行
			{
				if(m==target)
				{
					return true;
				}
			}
			if(!flag)
			{
				if(target < matrix[mid][0])
				{
					r=mid-1;
				}
				else
				{
					l=mid+1;
				}
			}
		}
		return false;
	}
};
```
