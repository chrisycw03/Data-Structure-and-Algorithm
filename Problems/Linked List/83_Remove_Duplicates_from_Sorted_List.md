# Description

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

# Constraints

- The number of nodes in the list is in the range [0, 300].
- -100 <= Node.val <= 100
- The list is guaranteed to be sorted in ascending order.

# Thoughts

- 創建2個ListNode指標，用來刪除重複節點
- 如果下一個節點的值和當前節點的值相同，刪除下一個節點，不同則跳到下一個節點

```c
struct ListNode* deleteDuplicates(struct ListNode* head){
  if(head == NULL) return head;
  struct ListNode* cur = head;
	struct ListNode* nxt = head->next;
	
	while(nxt != NULL){
		if(nxt->val == cur->val){
			cur->next = nxt->next;
			free(nxt);
      nxt = cur->next;
		}else{
			cur = nxt;			
		  nxt = cur->next;
		}
	}
	return head;
}
```