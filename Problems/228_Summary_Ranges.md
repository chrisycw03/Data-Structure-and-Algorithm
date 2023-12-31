# Description

You are given a sorted unique integer array nums.

A range [a,b] is the set of all integers from a to b (inclusive).

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

- "a->b" if a != b
- "a" if a == b

# Constraints

- 0 <= nums.length <= 20
- -2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1
- All the values of nums are unique.
- nums is sorted in ascending order.

# Thoughts

- 遍歷陣列
	- 判斷當前元素是否與上一個元素連續
	- 利用start跟end兩個變量紀錄連續元素的起點跟終點
- 利用sprintf格式化輸出結果

```c
char ** summaryRanges(int* nums, int numsSize, int* returnSize){

	char **range = (char**)calloc(numsSize, sizeof(char*));
	int i = 0;
	int j = 0;
	int start, end;

	while(i < numsSize){
		range[j] = (char*)calloc(25, sizeof(char));

		start = nums[i];
		while(i < numsSize - 1 && nums[i + 1] == nums[i] + 1)
			++i;

		end = nums[i];

		if(start == end)
			sprintf(range[j], "%d", end);
		else
			sprintf(range[j], "%d->%d", start, end);
		++i;
		++j;
	}

	*returnSize = j;
	return range;
}
```
