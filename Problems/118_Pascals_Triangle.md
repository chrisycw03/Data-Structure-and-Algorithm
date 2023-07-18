# Description

Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:

# Thought

* 帕斯卡三角形，第i層元素j為第i-1層元素j和元素j-1之和

# Code

* C++
```cpp
class Solution
{
public:
    vector<vector<int>> generate(int numRows)
    {
        vector<vector<int>> res;
        for(int i = 0; i < numRows; ++i)
        {
            vector<int> elem(i + 1, 1);
            for(int j = 1; j < i; ++j)
            {
                elem[j] = res[i-1][j-1] + res[i-1][j];
            }
            res.push_back(elem);
        }
        return res;
    }
};
```

* C
```c
int** generate(int numRows, int* returnSize, int** returnColumnSizes)
{
    *returnSize = numRows;

    // 指針指向一個指針指向一個陣列，陣列表示每一層的元素個數
    *returnColumnSizes = (int*)calloc(*returnSize, sizeof(int));
    int **res = (int**)calloc(*returnSize, sizeof(int*));

    for(int i = 0; i < *returnSize; i++)
    {
        (*returnColumnSizes)[i] = i + 1;
        res[i] = (int*)calloc((*returnColumnSizes)[i], sizeof(int));
        res[i][0] = 1;
        res[i][i] = 1;
        for(int j = 1; j < i; j++)
        {
            res[i][j] = res[i-1][j] + res[i-1][j-1];
        }
    }
    return res;
}

```
