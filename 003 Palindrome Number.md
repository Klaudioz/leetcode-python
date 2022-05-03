# 003 Palindrome Number

## Problem

- Given an integer `x`, return `true` if `x` is palindrome integer.
- An integer is a **palindrome** when it reads the same backward as forward.
- For example, `121` is a palindrome while `123` is not.

- **Examples:**
	- **Input:** x = 121, **Output:** true
	- **Input:** x = -121, **Output:** false
	- **Input:** x = 10, **Output:** false

- **Constraints:**
	-   `-231 <= x <= 231 - 1`
	**Follow up:** Could you solve it without converting the integer to a string?
	
## Solution
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return (str(x) == str(x)[::-1])
            
solution = Solution()
print(solution.isPalindrome(121)) # True
print(solution.isPalindrome(-121)) # False
print(solution.isPalindrome(0)) # True
print(solution.isPalindrome(10)) # False
```
## Diagram
N/A

## Time complexity
- **_O(n)_**

## Space complexity
- **_O(1)_** because we used constant space.

## Solution (Without converting the int to a string)
```python
class Solution:
  def isPalindrome(self, x: int) -> bool:
    if x < 0:
      return False
    reverse = 0
    original = x
    while original:
      reverse = (reverse * 10) + (original % 10)
      original //= 10
    return x == reverse
            
solution = Solution()
print(solution.isPalindrome(121)) # True
print(solution.isPalindrome(-121)) # False
print(solution.isPalindrome(0)) # True
print(solution.isPalindrome(10)) # False
```