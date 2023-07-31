# Description

Given a string columnTitle that represents the column title as appears in an Excel sheet, return its corresponding column number.

# Constraints

- 1 <= columnTitle.length <= 7
- columnTitle consists only of uppercase English letters.
- columnTitle is in the range ["A", "FXSHRXW"].

# Thoughts

- 字母和數字轉換

```c
int titleToNumber(char *columnTitle){
	int i = 0;
	unsigned column_num = 0;
	while(columnTitle[i]){
		column_num = column_num * 26 + columnTitle[i] - 'A' + 1;
		++i;
	}
	return column;
}
```