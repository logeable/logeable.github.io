---
layout: post
title: Minimum Depth of Binary Tree
category: [leetcode,algorithm]
---

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

[https://oj.leetcode.com/problems/minimum-depth-of-binary-tree/](https://oj.leetcode.com/problems/minimum-depth-of-binary-tree/) 

<!--break-->

---

####注意当左右子树有一个位空时，此时根不是叶子节点，所以不能简单返回左右子树中较小的那个。
```c++
int minDepth(TreeNode *root)
{
	if(root==nullptr)
	{
		return 0;
	}
	if(root->left==nullptr&&root->right==nullptr)
	{
		return 1;
	}
	int u,v;
	u=v=numeric_limits<int>::max();
	if(root->left)
	{
		u=minDepth(root->left);
	}
	if(root->right)
	{
		v=minDepth(root->right);
	}
	return 1+(u<v?u:v);
}
```
