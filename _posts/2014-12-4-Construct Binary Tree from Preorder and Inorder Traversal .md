---
layout: post
title: Construct Binary Tree from Preorder and Inorder Traversal 
category: [leetcode,algorithm]
---

Given preorder and inorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree

[https://oj.leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/](https://oj.leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

---

####我提交下面代码后，提示 *Memory Limit Exceeded*
```c++
TreeNode *buildTree(vector<int> &preorder, vector<int> &inorder) 
{
	if (preorder.size() == 0)
	{
		return nullptr;
	}

	auto root = new TreeNode(preorder[0]);
	auto itrPos = find(inorder.begin(), inorder.end(), preorder[0]);
	vector<int> vlin(inorder.begin(),itrPos),vrin(itrPos+1,inorder.end());
	vector<int> vlpre(preorder.begin() + 1, preorder.begin() + 1 + vlin.size()), vrpre(preorder.begin() + 1 + vlin.size(),preorder.end());
	root->left = buildTree(vlpre,vlin);
	root->right = buildTree(vrpre,vrin);
	return root;
}
```
####上面问题的原因可能是使用了过多的vector，那么就使用迭代器，就可以了，代码如下：
```c++
TreeNode *buildTree(vector<int> &preorder, vector<int> &inorder) 
{
	return build(preorder.begin(), preorder.end(), inorder.begin(), inorder.end());
}
TreeNode *build(vector<int>::iterator preb, vector<int>::iterator pree, vector<int>::iterator inb, vector<int>::iterator ine)
{
	if (preb == pree)
	{
		return nullptr;
	}
	auto root = new TreeNode(*preb);
	auto itrPos = find(inb,ine, *preb);
	auto size = distance(inb,itrPos);
	root->left = build(preb + 1, preb + 1 + size, inb, itrPos);
	root->right = build(preb + 1 + size, pree, itrPos+1, ine);
	return root;
}
```