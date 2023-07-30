# Description

Given the root of a binary tree, return the postorder traversal of its nodes' values.

# Constraints

- The number of the nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

# Thoughts

- 後序遍歷

```c
void Travel(struct TreeNode *root, int *ret, int *returnSize)
{
	if(!root){
	return;
	}
	Travel(root->left, ret, returnSize);
	Travel(root->right, ret, returnSize);
	ret[(*returnSize)++] = root->val;

}

int* postorderTraversal(struct TreeNode* root, int* returnSize){
	*returnSize = 0;
	int *val = (int*)malloc(100 * sizeof(int));
	Travel(root, val, returnSize);
	return val;
}
```