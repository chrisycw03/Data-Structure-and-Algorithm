# Description

Given the roots of two binary trees p and q, write a function to check if they are the same or not.
Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

# Constraints

- The number of nodes in both trees is in the range [0, 100].
- -10<sup>4</sup> <= Node.val <= 10<sup>4</sup>

# Thoughts

- 運用Devide and conquer的概念
- 兩個二元樹相同可以分解為: 根的值相同且左子樹相同且右子樹相同
- 利用遞迴

```c
bool isSameTree(struct TreeNode* p, struct TreeNode* q){
	if(!p && !q) // 根同為空指針
		return true;
	if(!p || !q) // 只有一個為空指針
		return false;
	if(p->val != q->val) // 根的值不同
		return false;
	
	// 左子樹相同且右子樹相同
	return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
}
```
