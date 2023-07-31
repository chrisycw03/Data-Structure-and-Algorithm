# Description

Given an array nums of size n, return the majority element.
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

# Constraints

- n == nums.length
- 1 <= n <= 5 * 10^4
- -10^9 <= nums[i] <= 10^9

# Thoughts

- 暴力法: 紀錄每個元素出現的次數，需要用到兩個迴圈，時間複雜度為非線性
- 可運用Hash Table儲存元素出現的次數，降低時間複雜度
- 尋找集合中的多數元素，可以使用Moore's Voting演算法
	- 利用一個計數器和一個變量紀錄元素，當計數器為0時，變量紀錄目前的元素，計數器加1
	- 當出現與變量相同的元素則計數器+1，若不同則計數器減1
	- 因為對超過半數的元素而言，出現次數大於其他元素出現次數的總和，所以最後變量紀錄的元素一定是超過半數的元素

```c
int majorityElement(int* nums, int numsSize){
	int cnt = 0;
	int majority = nums[0];
	for(int i = 0; i < numsSize; ++i){
		if(cnt == 0)
			majority = nums[i];
		
		if(nums[i] == majority){
			++cnt;
		else
			--cnt;
	}
	return majority;
}
```