# Description

Given the root of a binary tree, return its maximum depth.
A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

# Constraints

- The number of nodes in the tree is in the range [0, 104].
- -100 <= Node.val <= 100

# Thoughts

- Divide and conquer
- 將問題分解:
	- 左右子樹的深度+1(根)
- 遞迴

```c
int maxDepth(struct TreeNode *root){
	if(root == NULL)
		return 0;
	int left = maxDepth(root->left);
	int right = maxDepth(root->right);
	
	return (left > right ? left : right) + 1;
}
```

