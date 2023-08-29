# Despcription

Given an integer array nums, find the subarray with the largest sum, and return its sum.

# Constraints

- 1 <= nums.length <= 10<sup>5</sup>
- -10<sup>4 <= nums[i] <= 10<sup>4</sup>

# Thought

* 運用Dynamic Programing
* 創建一個與目標陣列相同長度的陣列，用來儲存第i個元素之前最大子陣列的和
* 接下來需要將**第i個元素**和**當前最大子陣列的和**相加，得到一個新的子陣列和
	* 如果**兩者相加的和**大於**第i個元素**，代表**兩者相加的和**是目前的最大子陣列
	* 如果**兩者相加的和**小於**第i個元素**，代表**第i個元素**才是目前的最大子陣列
* 想法:依次用**第i個元素**和**當前最大子陣列**來進行比較，可以得知如果兩者相加仍然小於**第i個元素**，則**當前最大子陣列**並不再是**最大子陣列**，將由**第i個元素**重新開始計算

# Code

* C++
```cpp
class Solution
{
public:
    int maxSubArray(vector<int>& nums)
    {
        vector<int> maxSum(1, nums[0]);
        int curSum;
        for(int i = 1; i < nums.size(); i++)
        {
            curSum = (maxSum[i - 1] + nums[i], nums[i]);
            maxSum.push_back(curSum);
        }

        int res = maxSum[0];
        for(int i = 1; i < nums.size(); i++)
        {
            res = max(res, maxSum[i]);
        }
        return res;
    }
}
```

* C
```c
int maxSubArray(int* nums, int numsSize)
{
    int maxSum[numsSize];
    maxSum[0] = nums[0];
    int curSum;

    for(int i = 1; i < numsSize; i++)
    {
        curSum = maxSum[i - 1] + nums[i];
        if(curSum > nums[i])
        {
            maxSum[i] = curSum;
        }
        else
        {
            maxSum[i] = nums[i];
        }
    }

    int res = maxSum[0];
    for(int i = 1; i < numsSize; i++)
    {
        if(maxSum[i] > res)
        {
            res = maxSum[i];
        }
    }
    return res;
}

```
