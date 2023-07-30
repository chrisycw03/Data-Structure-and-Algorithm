# Description

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

# Constraints

- 1 <= haystack.length, needle.length <= 104
- haystack and needle consist of only lowercase English characters.

# Thoughts

- 暴力法搜尋子字串

```c
int strStr(char * haystack, char * needle){
	int i = 0, j = 0;
	while(haystack[i]){
		if(haystack[i] == needle[j]){
			i++;
			j++;
		} else {
			i = i - j + 1;
			j = 0;
		}
		if(!needle[j])
			return i - j;
	}
	return -1;
}
```