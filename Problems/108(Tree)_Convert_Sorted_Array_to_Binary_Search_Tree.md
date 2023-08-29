# Description

Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

# Constraints

- 1 <= nums.length <= 10<sup>4</sup>
- -10<sup>4</sup> <= nums[i] <= 10<sup>4</sup>
- nums is sorted in a strictly increasing order.

# Thoughts

- 平衡二元樹: 左右子樹高度差不超過1，
- 二元搜尋樹: 左子樹所有節點小於根的值，右子樹所有的節點大於根的值
- 陣列為遞增 --> 二元搜尋樹的根一定是中位數
- Divide and conquer: 
	- 先序遍歷
	- 將陣列以中位數分為左右兩部分，即左右子樹
	- 終點: 子陣列沒有元素，不需要再分解

```c
struct TreeNode* Build(int *nums, int l, int r){
	if(l > r) return; //子陣列沒有元素，不需要再分解
	int mid = (l + r) / 2; //計算中位數的位置
	struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
	root->val = nums[mid]; //中位數即為根的值
	root->left = Build(nums, l, mid - 1); //子陣列左半部為左子樹
	root->right = Build(nums, mid + 1, r); //子陣列右半部為右子樹
	
	return root;
}

struct TreeNode* sortedArrayToBST(int* nums, int numsSize){
	return Build(nums, 0, numsSize - 1);
}

```
