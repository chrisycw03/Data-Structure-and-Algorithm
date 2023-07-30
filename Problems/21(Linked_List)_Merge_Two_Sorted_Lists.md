# Description

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

# Constraints

- The number of nodes in both lists is in the range [0, 50].
- -100 <= Node.val <= 100
- Both list1 and list2 are sorted in non-decreasing order.

# Thoughts

- 建立一個ListNode指標用於合併兩個linked list
- 建立一個ListNode指標插入新節點

```c
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2){
	struct ListNode* list_merge = (struct ListNode*)malloc(sizeof(struct ListNode));
	struct ListNode* p = list_merge;
	
	while(list1 && list2){
		if(list1->val < list2->val){
			p->next = list1;
			list1 = list1->next;
		}else{
			p->next = list2;
			list2 = list2->next;
		}
		p = p->next;
	}
	
	if(list1) p->next = list1;
	else p->next = list2;

	return list_merge->next;
}
```