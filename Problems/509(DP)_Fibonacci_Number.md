# Description

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,
```
F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
```
Given n, calculate F(n).

# Constraints

- 0 <= n <= 30

# Thoughts

- 費波納西數列，利用Dynamic Programming
	- 第n個數的值為第n-1和第n-2的值的和

```c
int fib(int n){
    int a = 0; //第n-2個數
	int b = 1; //第n-1個數
	int c; //第n個數
	if(n == 0)
		return a;
	
	for(int i = 2; i <= n; i++){
		c = a + b;
		a = b;
		b = c;
	}
	return b;
}
```