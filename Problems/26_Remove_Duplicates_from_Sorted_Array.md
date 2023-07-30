# Description

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.
Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:
- Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
- Return k.

# Constraints

- 1 <= nums.length <= 3 * 104
- -100 <= nums[i] <= 100
- nums is sorted in non-decreasing order.

# Thoughts

- 題目要求"in-place"移除重複的元素，所以利用兩個counter紀錄目前讀到的位置和目前寫入的位置

```c
int removeDuplicates(int* nums, int numsSize){
	int i = 1, j = 0;
	while(i < numsSize){
		if(nums[i] == nums[j]){ //若重複則往後一個元素在比較
			i++;
		}else{
			nums[++j] = nums[i++]; //若不重複則將值依序寫入
		}
	}
	return (j+1);
}

```