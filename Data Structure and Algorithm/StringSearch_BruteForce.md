# 字串搜尋

- C標準函式庫 <string.h> 提供 ```char *strstr(const char *haystack, const char *needle)``` 函式，對 haystack 搜尋第一次出現 needle 的位置
- C++的 STL-string 提供搜尋操作 ```find()```, ```rfind()``` 的成員函式
- 如果不使用 C/C++ 提供的函式，操作字串的搜尋最簡單的方式為 Brute Force，也可以應用在其他串結構的搜尋

## Brute Force (暴力法)

- 目標 在字串 str 中搜尋 substr 第一次出現的位置
- 分別依序遍歷 str 和 substr 的字元，比較是否相同
	- 如果完成 substr 的遍歷，且與 str 所包含的字元和順序完全相同，回傳 substr 在 str 中第一次出現的位置
	- 如果出現字元不相同，substr 需要從頭開始遍歷，str 需要回溯到起始點的下一個位置
	
	```
	0 1 2 3 4 5 6 7
	b a a b c a b d	(str)
	        ^i
            
	    0 1 2
	    a b d		(substr)
	        ^j
	
	/ str[4] 的字元與 substr[4] 不同
	/ substr 從頭開始遍歷
	/ str 回溯到起始點的下一個位置
    / 這輪比較的起始點位置是 2，所以下一輪比較的起始點位置是 3
	/ 計算方式 i - j + 1 (4 - 2 + 1 = 3)
	
	0 1 2 3 4 5 6 7
	b a a b c a b d	(str)
	      ^i
    
	      0 1 2
	      a b d		(substr)
	      ^j
    ```

### C/C++
	
```c
int BruteForce(char *str, char *substr){
	int i = 0;
	int j = 0;
	
	while(1){
		if(str[i] == substr[j]){ // 如果當前字元相同，接著比較下一個字元
			i++;
			j++;
		} else {
			i = i - j + 1; // 如果字元不同，str回溯到起始點的下一個位置
			j = 0;	// substr從頭開始遍歷
		}
		
		if(substr[j] == '\0'){
			i -= j; // 這一輪比較地起始點，即substr第一次出現的位置
			break;
		}
		
		if(str[i] == '\0'){
			i = -1;
			break;
		}
	}
	
	return i;
}
```