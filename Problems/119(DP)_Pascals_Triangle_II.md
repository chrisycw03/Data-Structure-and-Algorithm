# Description

Given an integer rowIndex, return the rowIndexth (0-indexed) row of the Pascal's triangle.

# Thought

* 方法一:利用組合算出地i層的每個元素
	* 第i層第j個元素為C i取j
* 方法二:利用previous row計算current row的每個元素
* 方法一跟方法二的時間複雜度都是O[N<sup>2</sup>]，但是想法一在計算組合的時候會碰到數字相乘的積超過INT_MAX，需要使用unsigned類型
* 實際提交的結果方法二要快於方法一

# Code
```c
// 想法一
// 計算組合C i取j
int Conbination(int i, int j)
{
    int k = i - j;
    // 如果j > (i - j)，C i取j可以改為計算C i取(i - j)
    if(j > i - j)
    {
        j = i - j;
    }
    unsigned long res = 1; // 計算時相乘積會大於INT_MAX
    for(int k = 1; k <= j; ++k)
    {
        res = res * (i - k + 1) / k;
    }
    return res;
}

int* getRow(int rowIndex, int* returnSize)
{
    *returnSize = rowIndex + 1;
    int *ans = (int*)malloc((rowIndex + 1) * sizeof(int));
    ans[0] = 1;
    ans[rowIndex] = 1;
    for(int i = 1; i < rowIndex; ++i)
    {
        ans[i] = Conbination(rowIndex, i);
    }
    return ans;
}
```
```c
//想法二
int* getRow(int rowIndex, int* returnSize)
{
    *returnSize = rowIndex + 1;
    int *pre = (int*)malloc((rowIndex + 1) * sizeof(int));
    int *curr = (int*)malloc((rowIndex + 1) * sizeof(int));
    pre[0] = 1;
    if(rowIndex == 0)
        return pre;
    for(int i = 1; i <= rowIndex; ++i)
    {
        curr[0] = 1;
        curr[i] = 1;
        for(int j = 1; j < i; j++)
        {
            curr[j] = pre[j-1] + pre[j];
        }
        for(int j = 1; j <= i; j++)
        {
            pre[j] = curr[j];
        }

    }
    return curr;
}

