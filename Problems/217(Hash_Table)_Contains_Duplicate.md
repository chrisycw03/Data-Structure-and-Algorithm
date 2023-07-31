# Description

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

# Constraints

- 1 <= nums.length <= 10^5
- -10^9 <= nums[i] <= 10^9

# Thoughts

- 方法一: 排序後再遍歷可知重複元素
- 方法二: 利用Hash Table紀錄元素，查詢Hash Table時判斷元素是否出現過
	- 衝突處理: 開放定址，線性搜尋

```c
bool containsDuplicate(int* nums, int numsSize){
  const size_t hashSize = numsSize * 2;
  bool status[hashSize];
  int hash[hashSize];
  memset(status, 0, sizeof(status));
  size_t idx;
  size_t key;
  
  for(int i = 0; i < numsSize; ++i)
  {
    key = nums[i];
    idx = key % hashSize;

    while(status[idx])
    {
      if(hash[idx] == key)
        return true;
      if(++idx >= hashSize)
        idx = 0;
    }

    status[idx] = true;
    hash[idx] = nums[i];

  }

  return false;
}
```