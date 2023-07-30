# Description

Given a binary tree, determine if it is height-balanced.

# Constraints

- The number of nodes in the tree is in the range [0, 5000].
- -104 <= Node.val <= 104

# Thoughts

- Divide and conquer:
	- Divide: 判斷左子樹和右子樹高度差 <= 1
	- 終點: 空節點

```c
int getLevel(struct TreeNode* root){
	if(root == NULL)
		return 0;
	int left = getLevel(root->left);
	int right = getLevel(root->right);
	return (left > right ? left + 1 : right + 1);
}

bool isBalanced(struct TreeNode* root){
	if(root == NULL)
		return true;
	int diff = getLevel(root->left) - getLevel(root->right);
	if(diff < -1 || diff > 1) // depth difference larger than 1
		return false;
	return isBalanced(root->left) && isBalanced(root->right); // both left and right child trees are balanced
}
```