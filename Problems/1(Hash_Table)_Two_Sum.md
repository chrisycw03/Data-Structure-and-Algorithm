# Description

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

# Constraints

- 2 <= nums.length <= 104
- -109 <= nums[i] <= 109
- -109 <= target <= 109
- Only one valid answer exists.

# Thoughts

- 暴力法: 用兩個迴圈搜尋兩整數和是否等於目標值，時間複雜度O(N^2)
- 遇到搜尋的問題可以考慮用Hash Table降低時間複雜度
- Hash Table:
	- Hash Table如果太小，發生衝突問題頻率會上升，需要浪費時間在處理衝突
	- 處理衝突的方式: 線性的方式搜尋或儲存資料(開放定址, 線性搜尋)
		- 搜尋: 當目前位置已經有儲存資料，判斷是否是答案，如果不是則往後位移一個位置在做判斷，直到當前的位置沒有儲存資料為止
		- 儲存資料: 當目前位置已經有儲存資料，如果有儲存資料，則往後位移一個位置，直到當前的位置沒有儲存資料為止
```c
typedef struct Hash{ //定義Hash Table的結構
  bool status; //狀態: 是否有儲存資料
  int val;
  int location; //資料在陣列中的位置
}Hash;


int* twoSum(int* nums, int numsSize, int target, int* returnSize){
  int *ret = (int*)calloc(2, sizeof(int));
  *returnSize = 2;
  int hash_size = 2 * numsSize; // 使用兩倍的陣列長度，避免頻繁的衝突
  Hash *hash_table = (Hash*)calloc(hash_size, sizeof(Hash));
  int key;
  size_t index;

  for(int i = 0; i < numsSize; i++){
    key = target - nums[i]; //目前的值要符合總和=target的條件，另一個值為多少
    index = (unsigned)key % hash_size; //在Hash Table的位置
	
	//Hash Table目前的位置有儲存資料，則判斷是否為答案
    while(hash_table[index].status){ 
      if(hash_table[index].val == key){
        ret[0] = hash_table[index].location;
        ret[1] = i;
        return ret;
      }
      if(index++ >= hash_size)
        index = 0;
    }
	
	//將目前的值存入Hash Table
    index = (unsigned)nums[i] % hash_size;
    while(hash_table[index].status){
      if(index++ >= hash_size)
        index = 0;
    }
    hash_table[index].val = nums[i];
    hash_table[index].status = true;
    hash_table[index].location = i;
  }

  return ret;
}
```
	
