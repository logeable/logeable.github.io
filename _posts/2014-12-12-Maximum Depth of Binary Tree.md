---
layout: post
title: Maximum Depth of Binary Tree
category: [leetcode,algorithm]
---

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

[https://oj.leetcode.com/problems/maximum-depth-of-binary-tree/](https://oj.leetcode.com/problems/maximum-depth-of-binary-tree/) 

<!--break-->

---

```c++
class Solution {
public:
    int maxDepth(TreeNode *root) {
        if(!root)
        {
            return 0;
        }
        int left=maxDepth(root->left);
        int right=maxDepth(root->right);
        return left<right?(right+1):(left+1);
    }
};
```
