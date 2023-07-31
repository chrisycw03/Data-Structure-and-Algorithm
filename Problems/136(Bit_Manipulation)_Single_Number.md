# Description

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.
You must implement a solution with a linear runtime complexity and use only constant extra space.

# Constraints

- 1 <= nums.length <= 3 * 104
- -3 * 104 <= nums[i] <= 3 * 104
- Each element in the array appears twice except for one element which appears only once.

# Thoughts

- 題目要求時間複雜度必須是線性的
- 利用(^)XOR邏輯運算符的特性: a^a = 0，將陣列所有元素相互以XOR運算，出像兩次的元素會被抵銷

```c
int singleNumber(int* nums, int numsSize){
	int ans = nums[0];
	while(--numsSize)
		ans = ans ^ nums[numsSize];
	return ans;
}
```