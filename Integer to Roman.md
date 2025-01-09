# 🏺 [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)

## 📜 Problem Statement

Roman numerals are represented by the following symbols and values:

| Symbol | Value |
|--------|-------|
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

**Rules**:
1. **Maximal Subtraction**:
   - For values not starting with `4` or `9`, append the maximal Roman symbol that can be subtracted from the current value.
   - E.g., for `8`, append `V` (5) and then `III` (3).

2. **Subtractive Notation**:
   - For values starting with `4` or `9`, use subtractive forms:
     - 4 → `IV` (1 less than 5).
     - 9 → `IX` (1 less than 10).
     - Similarly, for 40 (`XL`), 90 (`XC`), 400 (`CD`), and 900 (`CM`).

3. **Symbol Limitations**:
   - Powers of 10 (`I`, `X`, `C`, `M`) can be appended at most 3 times consecutively.
   - Symbols representing 5s (`V`, `L`, `D`) cannot repeat.

---

## 🔍 Examples

### Example 1:
**Input**: `num = 3749`  
**Output**: `"MMMDCCXLIX"`

**Explanation**:
- 3000 → `MMM` (1000 + 1000 + 1000).
- 700 → `DCC` (500 + 100 + 100).
- 40 → `XL` (10 less than 50).
- 9 → `IX` (1 less than 10).

---

### Example 2:
**Input**: `num = 58`  
**Output**: `"LVIII"`

**Explanation**:
- 50 → `L`.
- 8 → `VIII` (5 + 1 + 1 + 1).

---

### Example 3:
**Input**: `num = 1994`  
**Output**: `"MCMXCIV"`

**Explanation**:
- 1000 → `M`.
- 900 → `CM` (100 less than 1000).
- 90 → `XC` (10 less than 100).
- 4 → `IV` (1 less than 5).

---

## 💡 Approach

The problem is solved using **Greedy Algorithm**:

1. **Predefined Roman Symbols**:
   - Maintain mappings of Roman numeral symbols (`notation`) and their respective values (`numbers`).
   - Start from the largest value and subtract until the remaining number is less than the current Roman value.

2. **Algorithm Steps**:
   - Traverse from the largest Roman numeral value to the smallest.
   - Append symbols to the result as long as the current value can be subtracted.

3. **Return**:
   - After processing all values, return the resulting Roman numeral string.

---

## 🍩 Code Implementation (C++)

```cpp
#include <vector>
#include <string>
using namespace std;

class Solution {
public:
    string intToRoman(int num) {
        // Define Roman numeral symbols and their respective integer values
        vector<string> notation = {"I","IV","V","IX","X","XL","L","XC","C","CD","D","CM","M"};
        vector<int> numbers = {1,4,5,9,10,40,50,90,100,400,500,900,1000};
        
        // Start from the largest Roman numeral value
        int i = numbers.size() - 1; 
        string ans;

        // While there is still a number to convert
        while (num > 0) {
            if (num >= numbers[i]) { 
                // Append the corresponding Roman numeral symbol
                ans += notation[i]; 
                // Subtract the value from the number
                num -= numbers[i];  
            } else {
                // Move to the next smaller Roman numeral value
                i--; 
            }
        }

        return ans; // Return the resulting Roman numeral
    }
};
```

---

## ⚙️ Complexity Analysis

- **Time Complexity**: O(1)  
  Since the input range is limited to `[1, 3999]`, the algorithm performs a constant number of iterations.

- **Space Complexity**: O(1)  
  The storage required for the `notation` and `numbers` arrays is fixed.

---

## 🔥 Key Insights

1. **Greedy Approach**:
   - Roman numerals can be efficiently constructed by always subtracting the largest possible value.
   
2. **Predefined Rules**:
   - Subtractive forms are used only for specific cases (`4`, `9`, `40`, `90`, etc.).

---

Happy Coding! 🚀
