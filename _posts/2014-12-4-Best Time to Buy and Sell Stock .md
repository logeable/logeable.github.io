---
layout: post
title: Best Time to Buy and Sell Stock
category: [leetcode,algorithm]
---

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

[https://oj.leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://oj.leetcode.com/problems/best-time-to-buy-and-sell-stock/)

<!--break-->

---

####这一题容易出错的地方是这样求解，求出最大和最小值，然后相减，但是这一题最小值必须在最大值前面，因为不可能在最贵的时候买入，在最便宜的是活卖出。
```c++
int maxProfit(vector<int> &prices) 
{
	if (prices.size() == 0)
	{
		return 0;
	}
	int max, min;
	max = min = prices[0];
	for (auto m : prices)
	{
		if (m>max)
		{
			max = m;
		}
		if (min<m)
		{
			min = m;
		}
	}
	return max - min;
}
```
####知道这一点后很容易用O^2求解
```c++
int maxProfit(vector<int> &prices)
{
	int max = 0;
	for (int i = 0; i < prices.size(); i++)
	{
		for (int j = i; j < prices.size(); j++)
		{
			if (prices[j] - prices[i]>max)
			{
				max = prices[j] - prices[i];
			}
		}
	}
	return max;
}
```
####但是毫无疑问会超时，下面是用贪心算法将复杂度降低至O(n).
```c++
int maxProfit(vector<int> &prices)
{
	int max = 0;
	int s, e;
	s = e = 0;
	for (e = 0; e<prices.size(); e++)
	{
		int d = prices[e] - prices[s];
		if (d<0)
		{
			s = e;
		}
		if (d>max)
		{
			max = d;
		}
	}
	return max;
}
```
