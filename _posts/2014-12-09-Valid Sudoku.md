---
layout: post
title: Valid Sudoku
category: [leetcode,algorithm]
---

Determine if a Sudoku is valid, according to: [Sudoku Puzzles - The Rules](http://sudoku.com.au/TheRules.aspx).

The Sudoku board could be partially filled, where empty cells are filled with the character```'.'```.

![sudoku]({{ site.baseurl }}/images/Valid Sudoku/sudoku.png)

A partially filled sudoku which is valid.

Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.

[https://oj.leetcode.com/problems/valid-sudoku/](https://oj.leetcode.com/problems/valid-sudoku/) 

<!--break-->

---

####就是判断每一行，每一列，每一个九宫格里有没有乡同的数，有的话则返回false,否则返回true。虽然有点丑陋。。。不过还是ac了。
```c++
class Solution 
{
public:
    bool isValid(vector<char> &v)
    {
	    sort(v.begin(),v.end());
    	int s=v.size();
    	auto e=unique(v.begin(),v.end());
	    return e-v.begin()==s;
    }
    bool isValidSudoku(vector<vector<char> > &board) {
        for(int i=0;i<9;i++)
        {
            vector<char> v;
            for(int j=0;j<9;j++)
            {
                if(board[i][j]!='.')
                {
                    v.push_back(board[i][j]);
                }
            }
            if(!isValid(v))
            {
                return false;
            }
        }
        for(int i=0;i<9;i++)
        {
            vector<char> v;
            for(int j=0;j<9;j++)
            {
                if(board[j][i]!='.')
                {
                    v.push_back(board[j][i]);
                }
            }
            if(!isValid(v))
            {
                return false;
            }
        }
        for(int i=0;i<9;i+=3)
        {
            for(int j=0;j<9;j+=3)
            {
                vector<char> v;
                for(int m=0;m<3;m++)
                {
                    for(int n=0;n<3;n++)
                    {
                        if(board[m+i][n+j]!='.')
                        {
                            v.push_back(board[m+i][n+j]);
                        }
                    }
                }
                if(!isValid(v))
                {
                    return false;
                }
            }
        }
        return true;
    }
};
```
