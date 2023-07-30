# Description

# Constraints

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