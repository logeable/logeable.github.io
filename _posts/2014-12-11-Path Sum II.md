---
layout: post
title: Path Sum II 
category: [leetcode,algorithm]
---

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:
Given the below binary tree and sum = 22,

<pre>
<code>
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
</code>
</pre>

return

<pre>
<code>
[
   [5,4,11,2],
   [5,8,4,5]
]
</code>
</pre>

[https://oj.leetcode.com/problems/path-sum-ii/](https://oj.leetcode.com/problems/path-sum-ii/)  

<!--break-->

---

####将所有路径种和为sum的路径添加到result中。
```c++
class Solution {
public:
    vector<vector<int> > pathSum(TreeNode *root, int sum) 
    {
        vector<vector<int>> vvi;
        vector<vector<int>> result;
        vector<int> v;
        getPaths(root,v,vvi);
        for(auto path:vvi)
        {
            if(accumulate(path.begin(),path.end(),0)==sum)
            {
                result.push_back(path);
            }
        }
        return result;
    }

    void getPaths(TreeNode *root,vector<int> v,vector<vector<int>> &vvi)
    {
        if(!root)
        {
            return;
        }
        if(!root->left&&!root->right)
        {
            v.push_back(root->val);
            vvi.push_back(v);
            return;
        }
        v.push_back(root->val);
        if(root->left)
        {
            getPaths(root->left,v,vvi);
        }
        if(root->right)
        {
            getPaths(root->right,v,vvi);
        }
    }
};
```
