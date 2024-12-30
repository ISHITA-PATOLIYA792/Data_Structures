# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
In this repository, I share my daily solutions to LeetCode problems. Each solution includes well-commented code and detailed explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or an experienced coder, this repository is designed to inspire learning and improve problem-solving skills.

> **Daily Challenge** 💪: One problem, every single day! 🚀

---

## 🚀 Problem: [**189. Rotate Array**](https://leetcode.com/problems/rotate-array/)

### 📝 **Problem Description**

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

---

### 🏆 **Example Test Cases**

#### Example 1:

**Input:**  
`nums = [1,2,3,4,5,6,7], k = 3`

**Output:**  
`[5,6,7,1,2,3,4]`

**Explanation:**  
- Rotate 1 step to the right: `[7,1,2,3,4,5,6]`
- Rotate 2 steps to the right: `[6,7,1,2,3,4,5]`
- Rotate 3 steps to the right: `[5,6,7,1,2,3,4]`

#### Example 2:

**Input:**  
`nums = [-1,-100,3,99], k = 2`

**Output:**  
`[3,99,-1,-100]`

**Explanation:**  
- Rotate 1 step to the right: `[99,-1,-100,3]`
- Rotate 2 steps to the right: `[3,99,-1,-100]`

---

### 💡 **Solution Explanation**

This solution creates a temporary array to store the rotated elements, calculates the new positions for each element, and then overwrites the original array with the rotated values.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>

class Solution {
public:
    void rotate(std::vector<int>& nums, int k) {
        int n = nums.size();  // Get the size of the array
        k = k % n;  // Handle cases where k is greater than the size of the array

        std::vector<int> rotate(n);  // Temporary array to store rotated elements

        // Re-position each element to its new index
        for (int i = 0; i < n; i++) {
            rotate[(i + k) % n] = nums[i];
        }

        // Copy the rotated values back to the original array
        for (int i = 0; i < n; i++) {
            nums[i] = rotate[i];
        }
    }
};
