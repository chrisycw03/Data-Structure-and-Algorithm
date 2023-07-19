# Queue基本操作

- 先進先出(FIFO)
- 只能在queue後端加入新資料，前端移除資料
- 儲存結構
	- 陣列或linked list儲存
	- ```front``` 表示queue前端位置
	- ```rear``` 表示queue後端的下一個位置
- 基本操作
	- ```EnQueue()``` 後端加入新資料
	- ```DeQueue()``` 前端刪除新資料
	- ```IsEmpty()``` 判斷queue是否為空，front和rear位置重合表示queue為空
	- ```OverFlow``` queue已經沒有空間，此時加入新資料將造成溢位
	- 循環佇列 解決以陣列儲存的queue容易Overflow的問題
- 應用
	- 緩衝區
	- 廣度優先遍歷(BFS)
	
```c
// BFS
#define MAXSIZE 10
#define OVERFLOW -1

typedef struct TreeNode{
	int val;
	struct TreeNode* left;
	struct TreeNode* right;
} TreeNode;

void BFS(TreeNode* root){
	TreeNode* que[MAXSIZE];
	int front = 0;
	int rear = 0;
	que[rear++] = root;
	
	// 運用循環佇列
	while((front + 1) % MAXSIZE != rear){
		que[rear] = front->left; // 將left加入queue
		rear = (rear + 1) % MAXSIZE;
		if(rear == front) exit(OVERFLOW); // 判斷是否overflow
		
		que[rear] = front->right; // 將right加入queue
		rear = (rear + 1) % MAXSIZE;
		if(rear == front) exit(OVERFLOW); // 判斷是否overflow
		
		printf("%d ", front->val); // 操作節點
		front = (front + 1) % MAXSIZE; // 將root移出queue
	}
}
```