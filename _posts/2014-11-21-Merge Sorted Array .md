---
layout: post
title: Merge Sorted Array
category: [leetcode,algorithm]
---

Given two sorted integer arrays A and B, merge B into A as one sorted array.

Note:
You may assume that A has enough space (size that is greater or equal to m + n) to hold additional elements from B. The number of elements initialized in A and B are m and n respectively.
[https://oj.leetcode.com/problems/merge-sorted-array/](https://oj.leetcode.com/problems/merge-sorted-array/) 

---

```c++
class Solution {
public:
    void merge(int A[], int m, int B[], int n) {
        int i=0,j=0;
        int *C=new int[m+n];
        while(i<m&&j<n)
        {
            if(A[i]<B[j])
            {
                C[i+j]=A[i];
                i++;
            }
            else
            {
                C[i+j]=B[j];
                j++;
            }
        }
        while(i<m)
        {
            C[i+j]=A[i];
            i++;
        }
        while(j<n)
        {
            C[i+j]=B[j];
            j++;
        }
        for(i=0;i<m+n;i++)
        {
            A[i]=C[i];
        }
    }
};
```
