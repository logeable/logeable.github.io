---
layout: post
title: Length of Last Word
category: [leetcode,algorithm]
---

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

For example, 
Given s = "Hello World",
return 5.

[https://oj.leetcode.com/problems/length-of-last-word/](https://oj.leetcode.com/problems/length-of-last-word/) 

<!--break-->

---

####注意把尾部的空格忽略掉
```c++
class Solution {
public:
    int lengthOfLastWord(const char *s) {
        int len=0;
        int start=strlen(s)-1;
        while(s[start]==' ')
        {
            start--;
        }
        for(int i=start;i>=0&&s[i]!=' ';i--)
        {
            len++;
        }
        return len;
    }
};
```
