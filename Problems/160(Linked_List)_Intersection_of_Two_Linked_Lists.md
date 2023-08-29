# Description

Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

# Constraints

- The number of nodes of listA is in the m.
- The number of nodes of listB is in the n.
- 1 <= m, n <= 3 * 10<sup>4</sup>
- 1 <= Node.val <= 10<sup>5</sup>
- 0 <= skipA < m
- 0 <= skipB < n
- intersectVal is 0 if listA and listB do not intersect.
- intersectVal == listA[skipA] == listB[skipB] if listA and listB intersect.

# Thoughts

- 如果linked list相交，最後一個節點必相同
- 相交的位置只有可能是較短linked list的頭節點和之後的節點
- 先遍歷linked list，確認最後一個節點相同，並取得linked list長度LengthA, LengthB
- 從尾端往前較短"link list長度"的位置開始遍歷，即可判斷是否相交

```c
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB){
	if(headA == NULL || headB == NULL){
		return NULL;
	}
	
	struct ListNode* a = headA;
	struct ListNode* b = headB;
	int lengthA = 1;
	int lengthB = 1;
	
	while(a->next != NULL){
		lengthA++;
		a = a->next;
	}
	
	while(b->next != NULL){
		lengthB++;
		b = b->next;
	}
	
	if(a != b){
		return NULL;
	}
	
	a = headA;
	b = headB;
	while(lengthA > lengthB){
		a = a->next;
		lengthA--;
	}
	
	while(lengthB > lengthA){
		b = b->next;
		lengthB--;
	}
	
	while(a){
		if(a == b){
			return a;
		}
		a = a->next;
		b = b->next;
	}
	
	return NULL;
}
```
