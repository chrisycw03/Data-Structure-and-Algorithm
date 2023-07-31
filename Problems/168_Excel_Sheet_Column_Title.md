# Description

Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.

# Constraints

- 1 <= columnNumber <= 2^31 - 1

# Thoughts

- 26個字母為循環，利用%運算符轉換
- 因為A對應的整數是1所以取模之前需要位移1

```c
#define MAXSIZE 8
char ans[8];

char * convertToTitle(int columnNumber){
	int temp;
	int i = 0;
	while(columnNumber > 0){
		ans[i++] = (columnNumber - 1) % 26 + 'A';
		columnNumber = (columnNumber - 1) / 26;
	}
	ans[i] = '\0';
	
	//反轉陣列
	for(int j = 0; j < i / 2; ++j){
		temp = ans[j];
		ans[j] = ans[i - j - 1];
		ans[i - j - 1] = temp;
	}
	return ans;
}
```