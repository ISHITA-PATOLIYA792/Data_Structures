# 🏺 [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)

## 📜 Problem Statement

Roman numerals are represented by seven different symbols:

| Symbol | Value |
|--------|-------|
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

Roman numerals are typically written from largest to smallest from left to right. However, some numbers use subtraction instead of addition. For example:
- `IV` (4): `I` before `V` means subtract 1 from 5.
- `IX` (9): `I` before `X` means subtract 1 from 10.
- `XL` (40): `X` before `L` means subtract 10 from 50.
- `XC` (90): `X` before `C` means subtract 10 from 100.
- `CD` (400): `C` before `D` means subtract 100 from 500.
- `CM` (900): `C` before `M` means subtract 100 from 1000.

**Task**: Given a Roman numeral `s`, convert it to an integer.

---

## 🔍 Examples

### Example 1:
**Input:**  
`s = "III"`  
**Output:**  
`3`  

**Explanation:**  
`III = 3` (1 + 1 + 1).

### Example 2:
**Input:**  
`s = "LVIII"`  
**Output:**  
`58`  

**Explanation:**  
`L = 50`, `V = 5`, `III = 3` → `50 + 5 + 3 = 58`.

### Example 3:
**Input:**  
`s = "MCMXCIV"`  
**Output:**  
`1994`  

**Explanation:**  
- `M = 1000`
- `CM = 900`
- `XC = 90`
- `IV = 4`  
Total = `1000 + 900 + 90 + 4 = 1994`.

---

## 💡 Approach

The algorithm processes each character of the Roman numeral string.  

### Steps:
1. **Initialize `sum`**: Start with `sum = 0` to accumulate the integer value.
2. **Traverse the string**: For each character:
   - If the current numeral should be subtracted (e.g., `I` before `V`), subtract its value.
   - Otherwise, add its value.
3. **Check next character**: For subtraction cases (`IV`, `IX`, etc.), compare the current numeral with the next one.

### Observations:
- Subtraction occurs when:
  - `I` precedes `V` or `X`.
  - `X` precedes `L` or `C`.
  - `C` precedes `D` or `M`.

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <string>
using namespace std;

class Solution {
public:
    int romanToInt(string s) {
        int sum = 0; // Initialize the result variable to accumulate the integer value.

        // Loop through each character in the Roman numeral string.
        for (int i = 0; i < s.length(); i++) {
            switch (s[i]) { // Check the current Roman numeral.
                case 'I': { // 'I' can be 1 or -1 (if it forms 'IV' or 'IX').
                    // Check if the next character requires subtraction.
                    if (i < s.length() - 1 && (s[i + 1] == 'V' || s[i + 1] == 'X')) {
                        sum -= 1; // Subtract 1 for 'IV' or 'IX'.
                    } else {
                        sum += 1; // Add 1 for 'I'.
                    }
                    break;
                }
                case 'V': { // 'V' is always 5.
                    sum += 5;
                    break;
                }
                case 'X': { // 'X' can be 10 or -10 (if it forms 'XL' or 'XC').
                    // Check if the next character requires subtraction.
                    if (i < s.length() - 1 && (s[i + 1] == 'L' || s[i + 1] == 'C')) {
                        sum -= 10; // Subtract 10 for 'XL' or 'XC'.
                    } else {
                        sum += 10; // Add 10 for 'X'.
                    }
                    break;
                }
                case 'L': { // 'L' is always 50.
                    sum += 50;
                    break;
                }
                case 'C': { // 'C' can be 100 or -100 (if it forms 'CD' or 'CM').
                    // Check if the next character requires subtraction.
                    if (i < s.length() - 1 && (s[i + 1] == 'D' || s[i + 1] == 'M')) {
                        sum -= 100; // Subtract 100 for 'CD' or 'CM'.
                    } else {
                        sum += 100; // Add 100 for 'C'.
                    }
                    break;
                }
                case 'D': { // 'D' is always 500.
                    sum += 500;
                    break;
                }
                case 'M': { // 'M' is always 1000.
                    sum += 1000;
                    break;
                }
            }
        }

        return sum; // Return the accumulated sum as the integer representation of the Roman numeral.
    }
};
