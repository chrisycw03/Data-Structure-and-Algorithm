# Description

Given the head of a singly linked list, reverse the list, and return the reversed list.

# Constraints

- The number of nodes in the list is the range [0, 5000].
- -5000 <= Node.val <= 5000

# Thoughts

- 利用previous, current, next指標操作linked list

```c
struct ListNode* reverseList(struct ListNode* head){
	struct ListNode* prv = NULL;
	struct ListNode* cur = head;
	struct ListNode* nxt = head;
	
	while(cur != NULL){
		nxt = cur->next;
		cur->next = prv;
		
		prv = cur;
		cur = nxt;
	}
	
	return prv;
}
```