# 🚀 [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

## 📜 Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

### Constraints:
- The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.
- You **must not** use the division operation.
- Your algorithm must run in **O(n)** time complexity.

---

### 🔍 Examples

#### Example 1:
**Input:**  
`nums = [1,2,3,4]`  
**Output:**  
`[24,12,8,6]`  

#### Example 2:
**Input:**  
`nums = [-1,1,0,-3,3]`  
**Output:**  
`[0,0,9,0,0]`  

---

## 💡 Approach

The problem is solved using the **Prefix and Suffix Product Approach**.  

1. Create two auxiliary arrays:
   - `left_Product`: Stores the product of all elements to the left of `nums[i]`.
   - `right_Product`: Stores the product of all elements to the right of `nums[i]`.
2. Compute the prefix product in a forward pass.
3. Compute the suffix product in a backward pass.
4. Combine `left_Product` and `right_Product` to compute the final result for each index.

This approach ensures **O(n)** time complexity with **O(n)** space complexity.

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> ans(n);          // Output array
        vector<int> left_Product(n); // Prefix product array
        vector<int> right_Product(n);// Suffix product array

        // Calculate prefix products
        left_Product[0] = 1; // No elements to the left of the first element
        for (int i = 1; i < n; i++) {
            left_Product[i] = left_Product[i - 1] * nums[i - 1];
        }

        // Calculate suffix products
        right_Product[n - 1] = 1; // No elements to the right of the last element
        for (int i = n - 2; i >= 0; i--) {
            right_Product[i] = right_Product[i + 1] * nums[i + 1];
        }

        // Calculate the product of prefix and suffix for each index
        for (int i = 0; i < n; i++) {
            ans[i] = left_Product[i] * right_Product[i];
        }

        return ans;
    }
};
