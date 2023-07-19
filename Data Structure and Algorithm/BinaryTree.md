# Binary Tree

## Binary Tree Traversal

- Preorder Traversal
- Inorder Traversal
- Postorder Traversal
- Breadth-First Search (BFS)

### 方法

- Recursion
- Loop
	- DFS: 利用stack
	- BFS: 利用queue
	
```c
//Traverse by recursion

typedef struct TreeNode{
	int val;
	struct TreeNode* left;
	struct TreeNode* right;
} TreeNode;

// 遍歷過程可以分解為訪問左子樹、訪問右子樹，遞迴的終點為空節點
// 先操作root，接著訪問左子樹，最後訪問右子樹
void PreOrderTraverse(struct TreeNode* root){
	if(root == NULL) return; // 空節點返回
	
	printf("%d ", root->val); // 操作root
	PreOrderTraverse(root->left); // 訪問left
	PreOrderTraverse(root->right); // 訪問right
}

// 先訪問左子樹，接著操作root，最後訪問右子樹
void InOrderTraverse(struct TreeNode* root){
	if(root == NULL) return; // 空節點返回
	
	InOrderTraverse(root->left); // 訪問left
	printf("%d ", root->val); // 操作root
	InOrderTraverse(root->right); // 訪問right
}

// 先訪問左子樹，接著訪問右子樹，最後操作root
void PostOrderTraverse(struct TreeNode* root){
	if(root == NULL) return; // 空節點返回
	
	PostOrderTraverse(root->left); // 訪問left
	PostOrderTraverse(root->right); // 訪問right
	printf("%d ", root->val); // 操作root
}
```