# Description

Given the root of a binary tree, return the inorder traversal of its nodes' values.

# Constraints

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

# Thoughts

- 利用遞迴或Stack方式進行二元樹中序遍歷

```c
void Traverse(struct TreeNode *root, int *retList, int *returnSize){
  if(root == NULL) return;
  
  Traverse(root->left, retList, returnSize);
  retList[*returnSize] = root->val;
  ++*returnSize;
  Traverse(root->right, retList, returnSize);
}

int* inorderTraversal(struct TreeNode* root, int* returnSize){
  int *ret;
  ret = (int*)calloc(100, sizeof(int));
  *returnSize = 0;
  Traverse(root, ret, returnSize);
  
  return ret;
}
```