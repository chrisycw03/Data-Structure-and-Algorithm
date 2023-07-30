# Description

Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.

A leaf is a node with no children.

 
# Constraints

- The number of nodes in the tree is in the range [0, 5000].
- -1000 <= Node.val <= 1000
- -1000 <= targetSum <= 1000

# Thoughts

- 二元樹遍歷
- 遍歷到新的節點，則目標值減去節點的值做為新的目標值
- 一旦遍歷到葉子節點，則判斷是否與目標值相同

```c
bool hasPathSum(struct TreeNode* root, int targetSum){
	if(root == NULL)
		return false;
	
	if(root->left == NULL && root->right == NULL) //如果節點是葉子，則判斷總和是否等於目標
		return (targetSum == root->val);
	
	int new_target = targetSum - root->val;
	bool left_tree = hasPathSum(root->left, new_target);
	bool right_tree = hasPathSum(root->right, new_target);
	
	return left_tree || right_tree;
}
```