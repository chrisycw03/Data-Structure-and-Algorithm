# Description

Given the root of a binary tree, return the preorder traversal of its nodes' values.

# Constraints

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

# Thoughts

- 先序遍歷，遞迴或迴圈(Stack)

```c
void traversalArray(struct TreeNode *root, int *ret, int *i)
{
	if(!root)
	return;
	ret[(*i)++] = root->val;
	traversalArray(root->left, ret, i);
	traversalArray(root->right, ret, i); 
}

int* preorderTraversal(struct TreeNode* root, int* returnSize)
{
	*returnSize = 0;
	int *ans = malloc(100 * sizeof(int));
	traversalArray(root, ans, returnSize);
	return ans;
}
```