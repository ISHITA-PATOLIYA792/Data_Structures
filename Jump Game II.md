# 🎯 [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/)

## 📜 Problem Statement

You are given a **0-indexed array** of integers `nums` of length `n`.  
You are initially positioned at `nums[0]`.  

Each element `nums[i]` represents the **maximum length of a forward jump** from index `i`.  
In other words, if you are at `nums[i]`, you can jump to any `nums[i + j]` where:  

- `0 <= j <= nums[i]`  
- `i + j < n`

Return the **minimum number of jumps** to reach `nums[n - 1]`.  
The test cases are generated such that it is always possible to reach `nums[n - 1]`.

---

### 🔍 Examples

#### Example 1:

**Input:**  
`nums = [2,3,1,1,4]`  
**Output:**  
`2`  

**Explanation:**  
Jump 1 step from index `0` to `1`, then 3 steps to the last index.

---

#### Example 2:

**Input:**  
`nums = [2,3,0,1,4]`  
**Output:**  
`2`  

**Explanation:**  
Jump 1 step from index `0` to `1`, then 3 steps to the last index.

---

## 💡 Approach

The solution uses a **greedy algorithm** to minimize the number of jumps:
1. Keep track of:
   - `f` (farthest index reachable in the current jump range).
   - `curr` (end of the current jump range).
   - `j` (number of jumps taken).
2. Iterate through the array:
   - Update `f` as the maximum reachable index.
   - When `i` reaches `curr`, increment `j` (since a jump is required), and update `curr` to `f`.
   - If `curr` reaches or exceeds the last index, break and return `j`.

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <vector>
#include <algorithm>
using namespace std;

class Solution {
public:
    int jump(vector<int>& nums) {
        int j = 0;        // Number of jumps taken
        int curr = 0;     // End of the current jump range
        int f = 0;        // Farthest reachable index
        for (int i = 0; i < nums.size() - 1; i++) {
            f = max(f, i + nums[i]);  // Update farthest index
            if (i == curr) {         // If end of current jump range is reached
                ++j;                 // Increment jump count
                curr = f;            // Update current jump range
                if (curr >= nums.size() - 1) {  // If last index is reachable
                    break;
                }
            }
        }
        return j;
    }
};
