# Description

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Note: A leaf is a node with no children.

# Constraints

- The number of nodes in the tree is in the range [0, 105].
- -1000 <= Node.val <= 1000

# Thoughts

- 將節點分類
	- 左右子樹皆為空 --> 終點
	- 左右子樹其一為空 --> 取不為空的子樹深度
	- 左右子樹皆不為空 --> 取兩者最小的深度

```c
int minDepth(struct TreeNode* root){
	if(root == NULL) // root為空 --> 深度為0
		return 0;
	else if(!root->left && !root->right) // 左右子樹皆為空 --> 深度為1(根)
		return 1;
  
	int left_depth = minDepth(root->left);
	int right_depth = minDepth(root->right);

	if(!root->left || !root->right) // 左右子樹其一為空 --> 取不為空的子樹深度
		return left_depth + right_depth + 1;
	else // 左右子樹皆不為空 --> 取最小深度
		return (left_depth < right_depth ? left_depth + 1 : right_depth + 1);
}
```