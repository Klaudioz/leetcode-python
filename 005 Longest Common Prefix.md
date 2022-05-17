---
aliases: 
tags: 
date created: Sunday, May 15th 2022, 7:22:05 pm
date modified: Tuesday, May 17th 2022, 7:19:07 am
title: 005 Longest Common Prefix
---

# 005 Longest Common Prefix

## Problem

- Write a function to find the longest common prefix string amongst an array of strings.
- If there is no common prefix, return an empty string `""`.

- **Examples:**
	- **Input:** strs = ["flower","flow","flight"], **Output:** "fl"
	- **Input:** strs = ["dog","racecar","car"], **Output:** "", **Explanation:** There is no common prefix among the input strings.

**Constraints:**
- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lower-case English letters.

## Solution

```python
from typing import List

class Solution:
  def longestCommonPrefix(self, str: List[str]) -> str:
    if str == []:
      return ''
    elif len(str) == 1:
      return str[0] # The longest common prefix of an array containing only one element is that element itself.
    str.sort() # Sort the string
    result = ''
    for i in range(len(str[0])): # Compare the first and the last string character by character.
      if str[0][i] == str[-1][i]: #  If the characters match, append the character to the result.
        result += str[0][i]
      else:
        break
    return result
    
solution = Solution()
print(solution.longestCommonPrefix(['flower','flow','flight'])) # fl
print(solution.longestCommonPrefix(['dog','racecar','car'])) # ""
print(solution.longestCommonPrefix(['geeksforgeeks', 'geeks', 'geek', 'geezer'])) # gee
print(solution.longestCommonPrefix(['', '', ''])) # ""
print(solution.longestCommonPrefix([''])) # ""
print(solution.longestCommonPrefix([])) # ""
print(solution.longestCommonPrefix(['Today'])) # "Today"
```

## Diagram

![](https://i.imgur.com/MqObWEu.gif|)

## Time Complexity

- **_O(n)_**: where n is the size of the bigger string in the list. The for is iterating once each character of the string, even when a break can finish the loop earlier.

## Space Complexity

- **_O(1)_**: used constant space.

## More Ideas

- Python has a built-in [commonprefix()](https://docs.python.org/3/library/os.path.html) function to solve the problem in single-line: `return os.path.commonprefix(strs)`
