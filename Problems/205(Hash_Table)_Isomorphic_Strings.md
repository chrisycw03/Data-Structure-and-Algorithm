# Description

Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

# Constraints

- 1 <= s.length <= 5 * 10^4
- t.length == s.length
- s and t consist of any valid ascii character.

# Thoughts

- 利用Hash Table紀錄字符上一次出現的位置
	- 兩字串s, t在相同位置的字元，上一次出現的位置必須相同才符合isomorphic

```c
bool isIsomorphic(char * s, char * t){
	int s_hash[128] = {0}; // ASCII Code共128碼
	int t_hash[128] = {0};
	for(int i = 0; i < size; i++){
		if(s_hash[s[i]] != t_hash[t[i]]) // 判斷相同位置的字元上一次出現的位置
			return false;
		s_hash[s[i]] = i + 1; // 更新hash table字元出現的位置
		s_hash[t[i]] = i + 1;
	}
	return true;
}
```