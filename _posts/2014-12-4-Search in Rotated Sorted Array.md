---
layout: post
title: Search in Rotated Sorted Array 
category: [leetcode,algorithm]
---

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

[https://oj.leetcode.com/problems/search-in-rotated-sorted-array/](https://oj.leetcode.com/problems/search-in-rotated-sorted-array/) 

<!--break-->

---

####看到题目的时候顺手写了个O(n)的顺序查找，居然也能通过
```c++
int search(int A[], int n, int target) 
{
	for(int i=0;i<n;i++)
	{
		if(target==A[i])
		{
			return i;
		}
	}
	return -1;
}
```
####其实还是可以用O(logn)的二分查找的
```c++
int search(int A[], int n, int target) 
{
	int l=0,r=n-1;
	int mid;
	while(l<=r)
	{
		mid=l+(r-l)/2;
		if(A[mid]==target)
		{
			return mid;
		}
		if(A[mid]>=A[l])
		{
			if(target>=A[l]&&target<A[mid])
			{
				r=mid-1;
			}
			else
			{
				l=mid+1;
			}
		}
		else
		{
			if(target>A[mid]&&target<=A[r])
			{
				l=mid+1;
			}
			else
			{
				r=mid-1;
			}
		}
	}
	return -1;
}
```
