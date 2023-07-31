# Description

Write a function that takes the binary representation of an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

# Constraints

- The input must be a binary string of length 32

# Thoughts

- 利用計數器來記錄位元為1的個數，每記錄一次將整數n右移一個位元，當n為0代表已經沒有1的位元

```c
int hammingWeight(uint32_t n){
	int ans = 0;
	while(n > 0){
		ans += (n & 1);
		n >>= 1;
	}
	return ans;
}
```