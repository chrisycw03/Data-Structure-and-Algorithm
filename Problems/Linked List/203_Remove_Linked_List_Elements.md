# Description

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

# Constraints

- The number of nodes in the list is in the range [0, 104].
- 1 <= Node.val <= 50
- 0 <= val <= 50

# Thoughts

- linked list操作通常會使用prev, current, next指標作為輔助
- 遍歷linked list刪除和val相同的ListNode

```C
struct ListNode* removeElements(struct ListNode* head, int val){
	struct ListNode* prv = (struct ListNode*)malloc(sizeof(struct ListNode));
	struct ListNode* cur = head;
	struct ListNode* nxt = head;
	prv->next = head;
	head = prv;
	while(cur != NULL){
		nxt = cur->next;
		if(cur->val == val){
			prv->next = nxt;
			free(cur);
		}else{
			prv = cur;
		}
		cur = nxt;
	}
	return head->next;
}
```

