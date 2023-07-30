# Description

Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.
 
# Constraints

- 0 <= x <= 231 - 1

# Thoughts

- 可利用二元搜尋法
- 直接使用math.h的sqrt函數

```c
int mySqrt(int x){
  int y = sqrt(x);
  return y;
}
```