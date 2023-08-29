# Description

Given the root of a binary tree, invert the tree, and return its root.

# Constraints

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

# Thoughts

- Divide and conquer
	- Divide: 左子樹和右子樹對調
	- 終點: 空節點

```c
struct TreeNode* invertTree(struct TreeNode* root){
	if(root == NULL)
		return root;
	struct TreeNode *temp = root->right;
	root->right = root->left;
	root->left = temp;
	invertTree(root->left);
	invertTree(root->right);
	return root;
}
```
