---
layout: post
title: Maximum Subarray
category: [leetcode,algorithm]
---

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [−2,1,−3,4,−1,2,1,−5,4],
the contiguous subarray [4,−1,2,1] has the largest sum = 6.

**More practice:**
If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

[https://oj.leetcode.com/problems/maximum-subarray/](https://oj.leetcode.com/problems/maximum-subarray/) 

<!--break-->

---

####最简单的当然是枚举所有子数组，复杂度为O(n^2),用贪心算法可以实现复杂度为O(n)。
```c++
class Solution {
public:
    int maxSubArray(int A[], int n) {
        int max=A[0];
        int curMax=A[0];
        for(int i=1;i<n;i++)
        {
            if(curMax<0)
            {
                curMax=0;
            }
            curMax+=A[i];
            if(curMax>max)
            {
                max=curMax;
            }
        }
        return max;
    }
};
```
