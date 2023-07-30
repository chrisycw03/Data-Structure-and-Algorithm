# Description

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.
Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:
- Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
- Return k.

# Constraints

- 0 <= nums.length <= 100
- 0 <= nums[i] <= 50
- 0 <= val <= 100

# Thoughts

- 題目要求"in-place"移除指定的元素，所以利用兩個counter紀錄目前讀到的位置和目前寫入的位置

```c
int removeElement(int* nums, int numsSize, int val){
	int j = 0;
	for(int i = 0; i < numsSize; i++){
		if(nums[i] != val){
			nums[j++] = nums[i];
		}
	}
	return j;
}
```