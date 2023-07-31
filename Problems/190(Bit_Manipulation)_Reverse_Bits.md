# Description

Reverse bits of a given 32 bits unsigned integer.

# Constraints

- The input must be a binary string of length 32

# Thoughts

- 利用AND和位移運算子，將位元反轉

```c
uint32_t reverseBits(uint32_t n) {
	uint32_t ans = 0;
	for(int i = 31; i >= 0; --i){
		ans |= (n & 1) << i;
		n >>= 1;
	}
	return ans;
}
```