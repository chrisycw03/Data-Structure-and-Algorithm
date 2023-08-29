# Description

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

# Constraints

- The number of nodes in the list is in the range [1, 10<sup>5</sup>].
- 0 <= Node.val <= 9

# Thoughts

- 利用一個陣列依序紀錄Linked List的值，再從陣列尾端往頭端與Linked List比較，判斷是否為palindrome
```c
bool isPalindrome(struct ListNode* head){

    int stack[100000] = {0};
    int top = 0;

    struct ListNode *ptr = head;

    while(head){
        stack[top++] = head->val;
        head = head->next;
    }

    while(ptr){
        if(ptr->val != stack[--top])
            return false;
        ptr = ptr->next;
    }
    return true;
}
```
