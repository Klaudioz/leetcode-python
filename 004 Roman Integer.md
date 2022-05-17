---
aliases: 
tags: 
date created: Thursday, May 5th 2022, 9:16:32 am
date modified: Tuesday, May 10th 2022, 9:23:52 pm
title: 004 Roman Integer
---

# 004 Roman Integer

## Problem

- Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

| **Symbol** | **Value** |
| ---------- | --------- |
| I          | 1         |
| V          | 5         |
| X          | 10        |
| L          | 50        |
| C          | 100       |
| D          | 500       |
| M          | 1000      |

- For example, `2` is written as `II` in Roman numeral, just two one's added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

- Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

- Given a roman numeral, convert it to an integer.

- **Examples:**
	- **Input:** s = "III", **Output:** 3, **Explanation:** III = 3.
	- **Input:** s = "LVIII", **Output:** 58, **Explanation:** L = 50, V= 5, III = 3.
	- **Input:** s = "MCMXCIV, **Output:** 1994, **Explanation:** M = 1000, CM = 900, XC = 90 and IV = 4.

- **Constraints:**

	- `1 <= s.length <= 15`
	- `s` contains only the characters `('I', 'V', 'X', 'L', 'C', 'D', 'M')`.
	- It is **guaranteed** that `s` is a valid roman numeral in the range `[1, 3999]`.
	

## Solution

```python
class Solution:
    def romanToInt(self, S: str) -> int:
        roman = {'I':1,'V':5,'X':10,'L':50,'C':100,'D':500,'M':1000} # Dictionary of roman numerals
        ans = 0 # Store result
        for i in range(len(S)-1,-1,-1): # Loop for each character from right to left
            if 4 * roman[S[i]] < ans: # Subtractive principle roman numerals
              ans -= roman[S[i]]
            else:
              ans += roman[S[i]]
        return ans
            
solution = Solution()
print(solution.romanToInt('III')) # 3
print(solution.romanToInt('IV')) # 4
print(solution.romanToInt('IX')) # 9
print(solution.romanToInt('LVIII')) # 58
print(solution.romanToInt('MCMXCIV')) # 1994
```

- The only really tricky thing about counting in roman numerals is when a numeral is used as a subtractive value rather than an additive value. Then, the easier way to iterate through roman numerals is from right to left.
- Since numbers generally increase in a roman numeral notation from right to left, any subtractive number must also be smaller than our current **ans**.
- So we can avoid the need for an extra variable here. We do run into the case of repeated numerals causing an issue (ie, **"III"**), but we can clear that by multiplying **num** by any number between **2** and **4** before comparing it to **ans**, since the numerals jump in value by increments of at least **5x**.

## Diagram

- Subtractive principle roman numerals:
	- If I comes before V or X, subtract 1 eg: IV = 4 and IX = 9
	- If X comes before L or C, subtract 10 eg: XL = 40 and XC = 90
	- If C comes before D or M, subtract 100 eg: CD = 400 and CM = 900
	

![](https://i.imgur.com/GcEhSVb.png)

## Time Complexity

- _O(1)_. There is a finite set of roman numerals, the maximum number possible number can be 3999, which in roman numerals is MMMCMXCIX.

## Space Complexity

- **_O(1)_**: used constant space.
