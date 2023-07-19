# Stack基本操作

- 後進先出(LIFO)
- 只能在stack頂端操作
- 儲存結構
	- 陣列或linked list儲存
	- ```top``` stack頂端的下一個位置
- 基本操作
	- ```Push()``` stack top元素移出stack
	- ```Pop()``` 將資料加入stack
	- ```IsEmpty()``` 判斷stack是否為空。以陣列方式儲存時，top = 0表示stack為空
- 應用
	- 呼叫函式
	- 深度優先遍歷(DFS)
	- 老鼠走迷宮

```c
// PreOrderTraversal
#define MAXSIZE 10

typedef struct TreeNode{
	int val;
	struct TreeNode* left;
	struct TreeNode* right;
} TreeNode;

void PreOrderTraversal(TreeNode* root){
	TreeNode* base[MAXSIZE] = {0};
	int top = 0;
	
	while(root != NULL || top != 0){
		if(root != NULL){
			printf("%d", root->val); // 操作root
			base[top++] = root; // 將root加入stack
			root = root->left; // 訪問left
		}else{
			root = base[--top]->right; // 訪問right 接著將root移出stack
		}
	}
}

```
