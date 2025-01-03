# 💧 [Water Overflow Problem - GFG](https://practice.geeksforgeeks.org/problems/water-overflow2431/1)

## 📜 Problem Statement

You are given a stack of water glasses arranged in the form of a Pascal triangle.  

- Each glass can hold **1 unit of water**.
- Overflow takes place such that after a glass fills to capacity, any excess water is equally distributed between the two glasses below it (left and right).
- John pours `K` units of water into the **topmost glass**.  
- You need to determine how much water is present in the `C`-th glass of the `R`-th row, rounded to **6 decimal places**.

### Constraints
- There are enough glasses to accommodate any overflow.

---

### 🔍 Examples

#### Example 1:
**Input:**  
`K = 3, R = 2, C = 1`  
**Output:**  
`1.000000`  

**Explanation:**  
After pouring `K=3` units of water:  
1. The top glass (`R=1, C=1`) overflows 2 units of water.  
2. These 2 units are equally distributed between the two glasses in the second row.  
   - `R=2, C=1` gets **1 unit** of water.  
   - `R=2, C=2` gets **1 unit** of water.  

---

#### Example 2:
**Input:**  
`K = 3, R = 2, C = 2`  
**Output:**  
`1.000000`  

**Explanation:**  
The second glass in the second row (`R=2, C=2`) gets **1 unit** of water after the overflow, as described above.

---

## 💡 Approach

The solution uses a **dynamic programming approach**:
1. Use a 2D array `v` to represent the glasses:
   - `v[i][j]` stores the amount of water in the `j`-th glass of the `i`-th row.
2. Pour `K` units of water into the topmost glass `v[0][0]`.
3. Traverse each glass:
   - If a glass overflows (`v[i][j] > 1`), distribute the excess water equally between the two glasses below:
     - Add half to `v[i+1][j]`.
     - Add half to `v[i+1][j+1]`.
4. Return the amount of water in the `C`-th glass of the `R`-th row (`v[R-1][C-1]`).

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    // Helper function to calculate water overflow
    double solve(vector<vector<double>> &v, int K, int R, int C) {
        v[0][0] = K; // Pour K units into the topmost glass

        // Traverse the glasses to handle overflow
        for (int i = 0; i < v.size(); i++) {
            for (int j = 0; j <= i; j++) {
                if (v[i][j] > 1) {
                    double overflow = v[i][j] - 1;
                    v[i][j] = 1; // Set current glass to its capacity
                    v[i+1][j] += overflow / 2; // Distribute to bottom-left glass
                    v[i+1][j+1] += overflow / 2; // Distribute to bottom-right glass
                }
            }
        }
        return v[R-1][C-1]; // Return the water in the specified glass
    }

    // Main function to solve the problem
    double waterOverflow(int K, int R, int C) {
        vector<vector<double>> v(K, vector<double>(K, 0)); // Create 2D array for glasses
        return solve(v, K, R, C); // Call helper function
    }
};
