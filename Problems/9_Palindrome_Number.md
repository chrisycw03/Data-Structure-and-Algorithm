# Description

Given an integer x, return true if x is a palindrome, and false otherwise.

# Constraints

- -231 <= x <= 231 - 1

# Thoughts

- 用一個int rev紀錄反轉後的x，判斷x是否和rev相等

```c
bool isPalindrome(int x){
	if(x < 0)
		return false;
	int temp = x;
	unsigned rev = 0;
	
	while(temp != 0){
		rev = rev * 10 + temp % 10;
		temp /= 10;
	}
	
	if(x == rev)
		return true;
	else
		return false;
}
```