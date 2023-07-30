# Description

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

# Constraints

- 1 <= strs.length <= 200
- 0 <= strs[i].length <= 200
- strs[i] consists of only lowercase English letters.

# Thoughts

- 依序用第一個string的每個char和其他string比較，若char不同則停止

```c
char *longestCommonPrefix(char **strs, int strsSize){
	int size = strlen(strs[0]) + 1;
	char *prefix = (char*)calloc(size, sizeof(char));
	for(int i = 0; i < size; i++){
		for(int j = 1; j < strsSize; j++){
			if(strs[0][i] != strs[j][i])
				return prefix;
		}
		prefix[i] = strs[0][i];
	}
	return prefix;
}
```