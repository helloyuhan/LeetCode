# Problem

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:
Input: 123, Output: 321

Example 2:
Input: -123, Output: -321

Example 3:
Input: 120, Output: 21

Note: Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

# Solution

## Idea

pop and push: pop the last digit and push it to the first iteratively

```python
# pop operation
pop = x % 10
x = x // 10

# push operation
rev = rev * 10 + pop
```

time complexity: `O(log(x))` because there are approximately `$\log_10(x)$` numbers of digits in x
space complexity: `O(1)`

## Code

```python
class Solution:
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        
        s = -1 if x < 0 else 1
        x = abs(x)
        rev = 0
        while x != 0:
            pop = x%10
            rev = rev*10 + pop
            x = x//10
        if rev*s > 2**31-1 or rev*s < -2**31: return 0
        return rev*s
```
