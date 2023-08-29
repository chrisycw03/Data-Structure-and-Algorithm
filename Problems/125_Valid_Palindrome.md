# Description

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
Given a string s, return true if it is a palindrome, or false otherwise.

# Constraints

- 1 <= s.length <= 2 * 10<sup>5</sup>
- s consists only of printable ASCII characters.

# Thoughts

- 判定是否為迴文，首先移除非數字和字母，並將字母全部轉為小寫
- 反轉字串，比較與原字串是否相同
- 使用string.h函數

```c
bool isPalindrome(char * s){
	int j = strlen(s) - 1;
	int i = 0;
	while(i < j){
		while(i < j && !isalnum(s[i])) //從頭開始遍歷，若char非數字或字母則跳過
			i++;
		while(i < j && !isalnum(s[j])) //存尾端開始遍歷，若char非數字或字母則跳過
			j--;
		if(tolower(s[i]) != tolower(s[j])) //將char轉為小寫，比較頭尾char是否相同
			return false;
		++i;
		--j;
	}
	return true;
}
```
