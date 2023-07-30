# Description

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.
 
# Constraints

- nums1.length == m + n
- nums2.length == n
- 0 <= m, n <= 200
- 1 <= m + n <= 200
- -109 <= nums1[i], nums2[j] <= 109

# Thoughts

- 將nums1和nums2最大的元素依序從nums1開始存入
- 用3個counter分別紀錄讀取nums1, nums2和寫入的位置

```c
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n){
	--m; //counter of nums1
    --n; //counter of nums2
    
    for (int k = nums1Size - 1; k >= 0; --k)
    {
        if(m >= 0 && n < 0) //當nums2的元素全部寫入
            break;
        else if(m < 0 && n >= 0){ //當nums1的元素全部寫入
            nums1[k] = nums2[n];
            --n;
        }else if(m >= 0 && n >= 0 && nums1[m] < nums2[n]){ 
			//當nums2的元素最大，從nums1開始後端寫入
            nums1[k] = nums2[n];
            --n;
        }else{ //當nums1的元素最大，從nums1後端開始寫入
            nums1[k] = nums1[m];
            --m;
        }
                
    }
}
```