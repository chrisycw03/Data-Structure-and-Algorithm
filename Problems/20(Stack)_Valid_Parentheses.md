# Description

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

# Constraints

- 1 <= s.length <= 104
- s consists of parentheses only '()[]{}'.

# Thoughts

- LIFO --> 利用stack資料結構

```c
bool isValid(char *s){
	char *stack = (char*)calloc(strlen(s), sizeof(char));
	int top = 0;
	
	while(*s){
		switch(*s){
		case '(':
		case '[':
		case '{':
			stack[top++] = *s; //push *s to stack
			break;
		case ')':
			if(top == 0 || stack[--top] != '(') //判斷 & pop stack
				return false;
			break;
		case ']':
			if(top == 0 || stack[--top] != '[') //判斷 & pop stack
				return false;
			break;
		case '}':
			if(top == 0 || stack[--top] != '{') //判斷 & pop stack
				return false;
			break;
		}
		s++;
	}
  return top == 0;
}
```