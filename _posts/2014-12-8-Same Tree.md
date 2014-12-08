---
layout: post
title: Same Tree
category: [leetcode,algorithm]
---

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

[https://oj.leetcode.com/problems/same-tree/](https://oj.leetcode.com/problems/same-tree/) 

<!--break-->

---

这个比较简单，遍历就行了。
```c++
bool isSameTree(TreeNode *p,TreeNode *q)
{
	if(p==q)
	{
		return true;
		if(p==nullptr&&q!=p||q==nullptr&&q!=p)
		{
			return false;
		}
		return p->val==q->val&&
			isSameTree(p->left,q->left)&&isSameTree(p->right,q->right);
	}
}
```
