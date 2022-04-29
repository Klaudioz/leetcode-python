# ZigZag Conversion

## Problem
- Leetcode problem [link](https://leetcode.com/problems/zigzag-conversion/)
- The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P     A     H     N
A  P  L  S  I  I  G
Y     I     R  
```
- And then read line by line: `"PAHNAPLSIIGYIR"`
- Write the code that will take a string and make this conversion given a number of rows:

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
```

**Examples:**
- **Input:** s = "PAYPALISHIRING", numRows = 3, **Output:** "PAHNAPLSIIGYIR"
```
P     A     H     N
A  P  L  S  I  I  G
Y     I     R  
```
- **Input:** s = "ALGORITHMOFTHEDAY", numRows = 4, **Output:** "ATHLIHTEGRMFDYOOA"  
```
A      T      H
L   I  H   T  E
G  R   M  F   D  Y
O      O      A
```
- **Input:** s = "A", numRows = 1, **Output:** "A"

**Constraints:**

-   `1 <= s.length <= 1000`
-   `s` consists of English letters (lower-case and upper-case), `','` and `'.'`.
-   `1 <= numRows <= 1000`

## Solution

```python
class Solution:  
  def convert(self, s: str, numRows: int) -> str:
    if(numRows < 2):  # If numRows=0 or 1, it should return the string without any modification
      return s  
    arr = ['' for i in range(numRows)] # Creating an empty array with size = numRows
    reverse = 1 # There are two directions: 1 = down and -1 = up
    currentRow = 0  # Its value will determine where the characters will be
    for i in s:  
      arr[currentRow] += i
      currentRow += reverse
      if currentRow==0 or currentRow == numRows-1:
        reverse *= -1
    return(''.join(arr)) # Show the entire array

solution = Solution()
print(solution.convert('PAYPALISHIRING', 3)) # PAHNAPLSIIGYIR
print(solution.convert('ALGORITHMOFTHEDAY', 4)) # ATHLIHTEGRMFDYOOA
print(solution.convert('A', 1)) # A
```

^61823e

# Diagram
![](https://i.imgur.com/X4AA9n6.png)

# Time complexity
**_O(n)_**: where n is the size of the input string. The for is iterating once each character of the string.

# Space complexity
**_O(n)_**:  The result is just the same string with a different character order, so there is no case where the answer is a bigger size than the original string.