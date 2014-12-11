---
layout: post
title: Binary Tree Preorder Traversal
category: [leetcode,algorithm]
---

Given a binary tree, return the preorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},
```
   1
    \
     2
    /
   3
```
return [1,2,3].

Note: Recursive solution is trivial, could you do it iteratively?

<!--break-->

---

####先来个递归
```c++
class Solution {
public:
    vector<int> preorderTraversal(TreeNode *root) {
        vector<int> vi;
        preorderTraversal(root,vi);
        return vi;
    }
    void preorderTraversal(TreeNode *root,vector<int> &v)
    {
        if(!root)
        {
            return;
        }
        v.push_back(root->val);
        preorderTraversal(root->left,v);
        preorderTraversal(root->right,v);
    }
};
```
####再来个非递归
```c++
class Solution {
public:
    vector<int> preorderTraversal(TreeNode *root) {
        if(!root)
        {
            return {};
        }
        stack<TreeNode*> st;
        vector<int> vi;
        st.push(root);
        while(!st.empty())
        {
            auto tmp=st.top();
            vi.push_back(tmp->val);
            st.pop();
            if(tmp->right)
            {
                st.push(tmp->right);
            }
            if(tmp->left)
            {
                st.push(tmp->left);
            }
        }
        return vi;
    }
};
```
