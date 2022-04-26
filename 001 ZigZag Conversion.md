---
tags: [String]
---

## Problem
- The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P    A    H    N  
A P L S I   I  G  
Y     I    R

- And then read line by line: `"PAHNAPLSIIGYIR"`
- Write the code that will take a string and make this conversion given a number of rows:

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
```

**Example 1:**

**Input:** s = "PAYPALISHIRING", numRows = 3  
**Output:** "PAHNAPLSIIGYIR"

**Example 2:**

**Input:** s = "PAYPALISHIRING", numRows = 4  
**Output:** "PINALSIGYAHRPI"  
**Explanation:**  
P       I   N  
A   L  S  I   G  
Y A   H  R  
P       I

**Example 3:**

**Input:** s = "A", numRows = 1  
**Output:** "A"

**Constraints:**

-   `1 <= s.length <= 1000`
-   `s` consists of English letters (lower-case and upper-case), `','` and `'.'`.
-   `1 <= numRows <= 1000`

## Solution

```python
class Solution:  
  def convert(self, s: str, numRows: int) -> str:
    if(numRows < 2):  
      return s  
    arr = ['' for i in range(numRows)]  
    direction = 'down'  
    row = 0  
    for i in s:  
      arr[row] += i  
      if row == numRows-1:  
        direction = 'up'  
      elif row == 0:  
        direction = 'down'  
      if(direction == 'down'):  
        row += 1  
      else:  
        row -= 1  
    return(''.join(arr))

solution = Solution()
print(solution.convert('PAYPALISHIRING', 3)) # PAHNAPLSIIGYIR
print(solution.convert('PAYPALISHIRING', 4)) # PINALSIGYAHRPI
print(solution.convert('A', 1)) # A
```

^61823e
