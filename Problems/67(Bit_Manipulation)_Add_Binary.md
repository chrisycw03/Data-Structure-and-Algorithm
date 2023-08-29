# Description

Given two binary strings a and b, return their sum as a binary string.

# Constraints

- 1 <= a.length, b.length <= 10<sup>4</sup>
- a and b consist only of '0' or '1' characters.
- Each string does not contain leading zeros except for the zero itself.

# Thoughts

- 首先判斷a, b字串較長的長度，接著建立一個(較長字串長度+1)的字串c
- 將a, b相加的結果存入c，並對c進行進位的運算
- 若最高位為零則返回(c+1)，否則返回c

```c
char * addBinary(char * a, char * b){
  int i = strlen(a) - 1;   
  int j = strlen(b) - 1;
  int k = (i > j ? i : j) + 1;
  char *p = (i > j ? a : b);
  char *c;
  c = (char*)calloc(k + 2, sizeof(char));
  memset(c, '0', k + 1);
  
  while(k > 0){
    
	//a, b相加
    if(i >= 0) {
      c[k] = c[k] + a[i] - '0';
      i--;
    }
    if (j >= 0){
      c[k] = c[k] + b[j] - '0';
      j--;
    }
    
	//進位
    if (c[k] > '1'){
      c[k - 1]++;
      c[k] -= 2;
    }
        
    k--;
  }
  
  if (c[0] == '1'){
    return c;
  } else {
    return (c + 1);
  }
}
```
