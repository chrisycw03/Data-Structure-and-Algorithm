# Description

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
You must write an algorithm with O(log n) runtime complexity.

# Constraints

- 1 <= nums.length <= 104
- -104 <= nums[i] <= 104
- nums contains distinct values sorted in ascending order.
- -104 <= target <= 104

# Thoughts

- 二元搜尋法

```c
int searchInsert(int* nums, int numsSize, int target){
	int high = numsSize - 1;
	int low = 0;
	int mid;
	while(low <= high){
		mid = (high + low) / 2;
		if(target == nums[mid])
			return mid;
		else if(target > nums[mid])
			low = mid + 1;
		else
			high = mid - 1;
	}
	return low;
}
```