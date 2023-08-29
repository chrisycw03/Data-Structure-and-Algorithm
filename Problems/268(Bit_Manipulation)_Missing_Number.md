# Description

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

# Constraints

- n == nums.length
- 1 <= n <= 10^4
- 0 <= nums[i] <= n
- All the numbers of nums are unique.

# Thoughts

- 利用邏輯運算^互斥的特性
	- 0^1^2^...^n ^ (nums[0]^nums[1]...^nums[n-1])重複的數互斥抵銷，結果為缺少的數

```c
int missingNumber(int* nums, int numsSize{
    int res = 0;
    for(int i = 0; i < numsSize; i++){
        res = res ^ (i + 1) ^ nums[i]; // 利用XOR抵銷重複的數
    }
    return res;
}
```