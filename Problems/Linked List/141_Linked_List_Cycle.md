# Description

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

# Constraints

- The number of the nodes in the list is in the range [0, 104].
- -105 <= Node.val <= 105
- pos is -1 or a valid index in the linked-list.

# Thought

- 創建2個指標，分別以不同步伐遍歷linked list，linked list存在cycle，步伐較快的指標會倒追步伐較慢的指標。

```c
bool hasCycle(struct ListNode *head) 
{
	struct ListNode* fast = head;
	struct ListNode* slow = head;
	
	while(fast != NULL && fast->next != NULL){
		fast = fast->next->next;
		slow = slow->next;
		if(fast == slow){
			return true;
		}
	}
	return false;
}
```