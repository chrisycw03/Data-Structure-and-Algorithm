# Description

Given two strings s and goal, return true if you can swap two letters in s so the result is equal to goal, otherwise, return false.

Swapping letters is defined as taking two indices i and j (0-indexed) such that i != j and swapping the characters at s[i] and s[j].

- For example, swapping at indices 0 and 2 in "abcd" results in "cbad".

# Constraints

- 1 <= s.length, goal.length <= 2 * 10<sup>4</sup>
- s and goal consist of lowercase letters.

# Thoughts

1. 判斷字串長度是否相等
2. 遍歷字串，紀錄字元不同的次數和位置
	- 第二次出現字元不同時，與前一次出現不同的字元交換位置
	- 如果出現超過三次不同字元，返回false
3. 判斷字元不同的次數
	- 次數0: 字串中有字元重複出現則返回true，否則返回false
	- 次數1: 返回false
4. 判斷交換字元後，兩字串是否相等

```c
bool buddyStrings(char * s, char * goal){
    if(strlen(s) != strlen(goal))
        return false;
    
    int diff_loc, diff_times = 0;
    int hash[26] = {0};
    bool duplicate = 0;
    char temp;
    
    for(int i = 0; i < strlen(s); i++){
        if(++hash[s[i] - 'a'] > 1)
            duplicate = 1;
        
        if(s[i] != goal[i]){
            switch(++diff_times){
            case 1:
                diff_loc = i;
                break;
            case 2:
                temp = s[i];
                s[i] = s[diff_loc];
                s[diff_loc] = temp;
                break;;
            default:
                return false;
            }
        }
    }

    if(diff_times == 0){
        if(duplicate > 0)
            return true;
        else
            return false;
    }else if(diff_times == 1){
        return false;
    }

    for(int i = 0; i < strlen(s); i++){
        if(s[i] != goal[i])
            return false;
    }
    return true;;
}
```
