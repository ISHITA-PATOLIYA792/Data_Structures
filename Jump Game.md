# 🎯 [55. Jump Game](https://leetcode.com/problems/jump-game/)

## 📜 Problem Statement

You are given an integer array `nums`.  
- You are initially positioned at the array's first index.  
- Each element in the array represents your **maximum jump length** at that position.  

Return `true` if you can reach the **last index**, or `false` otherwise.

---

### 🔍 Examples

#### Example 1:

**Input:**  
`nums = [2,3,1,1,4]`  
**Output:**  
`true`  

**Explanation:**  
Jump 1 step from index 0 to 1, then 3 steps to the last index.

---

#### Example 2:

**Input:**  
`nums = [3,2,1,0,4]`  
**Output:**  
`false`  

**Explanation:**  
You will always arrive at index 3 no matter what. Its maximum jump length is `0`, which makes it impossible to reach the last index.

---

## 💡 Approach

The solution uses a **greedy algorithm** to determine if the last index can be reached:
1. Keep track of the **maximum index** (`a`) that can be reached at any point.
2. If the current index exceeds `a`, it means it's impossible to proceed further.
3. If at any point `a` reaches or exceeds the last index, return `true`.

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <vector>
#include <algorithm>
using namespace std;

class Solution {
public:
    bool canJump(vector<int>& nums) {
        int n = nums.size();
        int a = 0;  // Maximum index reachable
        int f = 0;  // Flag to indicate success
        for (int i = 0; i < n; i++) {
            if (i > a) {  // If current index is beyond reachable
                f = 0;
                break;
            }
            a = max(a, i + nums[i]);  // Update maximum reachable index
            if (a >= n - 1) {  // If we can reach or exceed the last index
                f = 1;
                break;
            }
        }
        return f == 1;
    }
};
