# Description

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

# Constraints

- 1 <= s.length <= 15
- s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').
- It is guaranteed that s is a valid roman numeral in the range [1, 3999].

# Thoughts

- 用case判斷羅馬數字對應的值
- 根據規則: I, X, C可能代表正值或負值，需要利用其下一個位置的羅馬數字判斷正負

```c
int romanToInt(char *s){
	int res = 0;
	int size = strlen(s);
	for(int i = 0; i < size; i++){
		switch(s[i]){
		case 'I':
			if(i < size - 1 && (s[i+1] == 'V' || s[i+1] == 'X'))
				res += -1;
			else
				res += 1;
			break;
		case 'X':
			if(i < size - 1 && (s[i+1] == 'L' || s[i+1] == 'C'))
				res += -10;
			else
				res += 10;
			break;
		case 'C':
			if(i < size - 1 && (s[i+1] == 'D' || s[i+1] == 'M'))
				res += -100;
			else
				res += 100;
			break;
		case 'V':
			res += 5;
			break;
		case 'L':
			res += 50;
			break;
		case 'D':
			res += 500;
			break;
		case 'M':
			res += 1000;
			break;
		}
	}
	return res;
}
```