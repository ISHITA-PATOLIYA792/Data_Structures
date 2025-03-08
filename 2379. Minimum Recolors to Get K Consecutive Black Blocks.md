# 🚀 [2379. Minimum Recolors to Get K Consecutive Black Blocks](https://leetcode.com/problems/minimum-recolors-to-get-k-consecutive-black-blocks/)

## 📜 Problem Statement

You are given a **0-indexed string** `blocks` of length `n`, where:
- `blocks[i]` is either `'W'` (White) or `'B'` (Black), representing the color of the `i-th` block.

You are also given an **integer** `k`, which is the **desired number of consecutive black blocks**.

### ✨ Operation Allowed:
In **one operation**, you can **recolor** a `'W'` block into a `'B'`.

### 🎯 Objective:
Return the **minimum number of operations** needed so that there is at least **one occurrence** of `k` **consecutive** black blocks.

---

## 🔍 Examples

### Example 1:
**Input:**  
blocks = "WBBWWBBWBW", k = 7
3
blocks = "WBWBBBW", k = 2
0

```cpp
#include <string>
#include <algorithm>
using namespace std;

class Solution {
public:
    int minimumRecolors(string blocks, int k) {
        int n = blocks.size();
        int result = k;

        for (int i = 0; i <= n - k; i++) {
            int W = 0;
            for (int j = i; j < i + k; j++) {  // Window of size 'k'
                if (blocks[j] == 'W') {
                    W++;
                }
            }
            result = min(result, W);
        }

        return result;
    }
};
