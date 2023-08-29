# Description

Given an integer array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.

# Constraints

- 1 <= nums.length <= 10<sup>5</sup>
- -10<sup>9 <= nums[i] <= 10<sup>9</sup>
- 0 <= k <= 10<sup>5</sup>

# Thoughts

- 利用Hash Table紀錄元素，用另一個陣列紀錄上次同一元素出現的位置，判斷是否滿足條件

```c
bool containsNearbyDuplicate(int* nums, int numsSize, int k){
    size_t hashSize = numsSize * 2;
    int states[hashSize];
    int hash[hashSize];
    memset(states, 0, sizeof(states));
    memset(hash, 0, sizeof(hash));
    size_t idx;
    size_t key;
    size_t last;

    for(int i = 0; i < numsSize; ++i){
        key = nums[i];
        idx = key % hashSize;

        while(states[idx]){
			//當元素重複出現，判斷是否滿足兩個元素距離不大於k
            if(hash[idx] == nums[i]){
                last = (i + 1) - states[idx];
                if(last <= k)
                    return true;
            }
            if(++idx >= hashSize)
                idx = 0;
        }

        states[idx] = i + 1;
        hash[idx] = nums[i];
    }
    return false;
}
```
