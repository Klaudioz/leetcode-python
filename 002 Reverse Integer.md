# 002 Reverse Integer

## Problem
- Leetcode problem [link](https://leetcode.com/problems/reverse-integer).
- Given a signed 32-bit integer `x`, return `x` _with its digits reversed_. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.
- Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

- **Examples:**
	- **Input:** x = 123, **Output:** 321
	- **Input:** x = -123, **Output:** -321
	- **Input:** x = 120, **Output:** 21

**Constraints:**
-   `-2**31 <= x <= 2**31 - 1`

## Solution
```python
class Solution:
  def reverse(self, x: int) -> int:
    if x<0: # If number is negative
        x = int(str(x*-1)[::-1])*-1 # Make the number positive (multiplying by -1), convert it to string, revert it, convert back to number and multiply back by -1
    else:
        x = int(str(x)[::-1]) # Convert the number to string, revert it and convert it back to number
    if x >= -2**31 and x <= 2**31-1: # Constrain cases
        return x
    else:
        return 0

solution = Solution()
print(solution.reverse(123)) # 321
print(solution.reverse(-123)) # -321
print(solution.reverse(120)) # 21
print(solution.reverse(000)) # 0
print(solution.reverse(1000000003)) # 0. Returns zero in overflow case
```

## Diagram
N/A

## Time complexity
- `O(log n)` = **_O(1)_**

## Space complexity
- **_O(1)_** because we used constant space.

## Another methods
- Using `divide` and `mod` operations:
	- Extract last digit from right to left from the given number using the mod operator.
	- Put the extracted digit into its correct position in the result.
	- Discard the currently processed digit from the original number using divide operation.
	- Repeat steps 1 - 3 as long as the given value **x** is greater than 0.
-   pop and push
    -   pop:
        -   last_digit = x // 10
        -   x = x // 10 ## to update x
    -   push:
        -   y = y * 10 + last_digit