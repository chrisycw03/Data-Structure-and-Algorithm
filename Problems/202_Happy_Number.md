# Description

Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.

# Constraints

- 1 <= n <= 2^31 - 1

# Thoughts

- 規律: 只要遇到下列的數，會開始循環，所以不會是Happy number
	- 2, 4, 16, 37, 58, 89, 145, 42, 20

```c
bool isHappy(int n){
	int notHappy[9] = {2, 4, 16, 37, 58, 89, 145, 42, 20};
	int temp;
	while(n != 1){
		temp = 0;
		while(n > 0){ //計算每位數的平方和
			temp += (n % 10) * (n % 10);
			n /= 10;
		}
		
		for(int i = 0; i < 9; i++){ //判斷是否不為Happy Number
			if(temp == notHappy[i])
				return false;
			}
		}
		
		n = temp;
	}
	return true;
}
```