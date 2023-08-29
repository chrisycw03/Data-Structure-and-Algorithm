4# Description

Given two strings s and t, return true if t is an anagram of s, and false otherwise.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

# Constraints

- 1 <= s.length, t.length <= 5 * 104
- s and t consist of lowercase English letters.

# Thoughts

- 利用Hash Table紀錄每個字母出現的次數，比對兩個字串是否相同


```c
bool isAnagram(char * s, char * t){
	if(strlen(s) != strlen(t))
		return false;
	
	int hash_s[26] = {0};
	int hash_t[26] = {0};
	
	for(int i = 0; i < strlen(s); i++){ //紀錄字母出現次數
		hash_s[s[i] - 'a']++;
		hash_t[t[i] - 'a']++;
	}
	
	for(int i = 0; i < 26; i++){ //判斷母出現次數是否相同
		if(hash_s[i] != hash_t[i])
			return false;
	}
	return true;
}
```
