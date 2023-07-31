# Description

Given an integer n, return true if it is a power of two. Otherwise, return false.
An integer n is a power of two, if there exists an integer x such that n == 2^x.

# Constraints

- -2^31 <= n <= 2^31 - 1

# Thoughts

- 利用二進位特性，若整數為2的指數，在二進位中只會有一個位元為1
	- 用位移運算找到值為1的位元，若再位移一次後整數為0，表示整數為2的指數
```c
bool isPowerOfTwo(int n){
  if(n == 0)
    return false;

  while(!(n & 1)) //右位移運算到值為1的位元
    n >>= 1;

  if((n >> 1) == 0) //在往右位移一次，若為0表示為2的指數
    return true;
  return false;
}
```