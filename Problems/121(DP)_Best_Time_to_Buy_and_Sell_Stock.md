# Description

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

# Constraints

- 1 <= prices.length <= 10<sup>5</sup>
- 0 <= prices[i] <= 10<sup>4</sup>

# Thought

* Dynamic Programing
* 想法:紀錄**最低買價**和**最大收益**
	* 依序比較**每日股價**與**最低買價**，儲存新的**最低買價**
	* 依序計算**當日賣出的收益**和**目前最大收益**比較，儲存新的**最大收益**

# Code

* C++, C
```cpp
class Solution
{
public:
    int maxProfit(vector<int>& prices)
    {
        int buy = prices[0]; // 紀錄最低買價
        int profit = 0; // 紀錄最大收益

        for(int i = 1; i < prices.size(); i++)
        {
            // 如果今日賣出的收益大於原本的最大收益，今日賣出的收益即是最大收益
            if(profit < prices[i] - buy)
            {
                profit = prices[i] - buy;
            }
            
            // 如果今日股價小於原本的買價，今日股價即是最低買價
            if(prices[i] < buy)
            {
                buy = prices[i];
            }

        }
    }

}

```
