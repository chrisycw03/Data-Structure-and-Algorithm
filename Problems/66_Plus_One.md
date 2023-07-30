# Description

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

# Constraints

- 1 <= digits.length <= 100
- 0 <= digits[i] <= 9
- digits does not contain any leading 0's.

# Thoughts

```c
int* plusOne(int* digits, int digitsSize, int* returnSize){
	
	int i = digitsSize - 1;
	digits[i]++;

	for (i; i > 0 && digits[i] == 10; i--){ //進位
		digits[i] = 0;
		digits[i - 1]++;
	}

	if (digits[0] < 10){ //最高位<10 --> 位數沒有增加
		*returnSize = digitsSize;
		return digits;
	}

	*returnSize = digitsSize + 1; //位數增加
	int *returnDigits;
	returnDigits = (int*)malloc(*returnSize * sizeof(int));
	returnDigits[0] = 1;
	returnDigits[1] = 0;

	for (i = 1; i < digitsSize; i++){
		returnDigits[i + 1] = digits[i];
	}

	return returnDigits;
}
```