# Description

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

# Constraints

- 0 <= n <= 105

# Thoughts

- 遍歷並加總每個值為1的位元

```c
int* countBits(int n, int* returnSize){
    *returnSize = n + 1;
    int *res = (int*)calloc(*returnSize, sizeof(int));
    int temp;
    for(int i = 0; i < *returnSize; i++){
        temp = i;
        while(temp){
            res[i] += (temp & 1);
            temp >>= 1;
        }
    }
    return res;
}
```