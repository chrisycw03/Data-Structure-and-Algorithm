# Description

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

# Constraints

- 0 <= s.length <= 100
- 0 <= t.length <= 104
- s and t consist only of lowercase English letters.

# Thoughts

- 利用兩個計數器分別紀錄用來遍歷s, t
	- 當s的字元與t相同，s位移到下一個字元
	- 當t遍歷完成，若s也遍歷完則返回true，否則返回false

```c
bool isSubsequence(char * s, char * t){
    int i = 0, j = 0;
    while(t[j]){
        if(s[i] == t[j])
            i++;
        j++;
    }

    if(s[i])
        return false;
    else
        return true;
}
```