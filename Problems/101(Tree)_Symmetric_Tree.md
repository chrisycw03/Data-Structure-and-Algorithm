# Description

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

# Constraints

- The number of nodes in the tree is in the range [1, 1000].
- -100 <= Node.val <= 100

# Thoughts

- Devided and conquer
- 將問題分解:
	- 左子樹的根值 = 右子樹的根值
	- 左子樹的左子樹 對稱 右子樹的右子樹
	- 左子樹的右子樹 對稱 右子樹的左子樹
- 遞迴

```c
bool Mirror(struct TreeNode *tree1, struct TreeNode *tree2){
	if(!tree1 && !tree2) //左子樹和右子樹都為空
		return true;
	else if(!tree1 || !tree2) //左子樹和右子樹其中之一為空
		return false;
	
	//左右子樹的根值相同
	//左子樹的左子樹 對稱 右子樹的右子樹
	//左子樹的右子樹 對稱 右子樹的左子樹
	return (tree1->val == tree2->val) && Mirror(tree1->left, tree2->right) && Mirror(tree1->right, tree2->left);		
}

bool isSymmetric(struct TreeNode *root){
	if(root == NULL)
		return true;
	
	return Mirror(root->left, root->right);
}
```