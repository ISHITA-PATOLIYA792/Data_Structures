# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
Here, I share my daily solutions to LeetCode problems, with well-commented code and explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or experienced, this repo is meant to inspire learning and problem-solving.

> **Daily Coding Practice** 💪: **Boost your coding skills daily with new challenges ! Let’s keep coding, keep learning!** 🚀

---

## 🚀 Problem: **[27. Remove Element](https://leetcode.com/problems/remove-element/)**

### 📝 **Problem Description**

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` in-place. The order of the elements may be changed. Then, return the number of elements in `nums` which are not equal to `val`.

### **Input**
- An integer array `nums`
- An integer `val`

### **Output**
- An integer `k`, which represents the number of elements in `nums` that are not equal to `val`.

---

### 🏆 **Example Test Cases**

#### Example 1:
**Input:**  
`nums = [3, 2, 2, 3]`, `val = 3`  
**Output:**  
`k = 2`, `nums = [2, 2, _, _]`  
**Explanation:**  
The first two elements of `nums` will contain the value `2`. It does not matter what you leave beyond the returned `k` (hence the underscores).

#### Example 2:
**Input:**  
`nums = [0, 1, 2, 2, 3, 0, 4, 2]`, `val = 2`  
**Output:**  
`k = 5`, `nums = [0, 1, 4, 0, 3, _, _, _]`  
**Explanation:**  
The first five elements of `nums` will contain `0, 1, 4, 0, 3`. It does not matter what you leave beyond the returned `k` (hence the underscores).

---

### 💡 **Solution Explanation**

To solve this problem efficiently, we can use the two-pointer technique:

1. We initialize a pointer `j` at the start of the array `nums`.
2. Traverse the array using pointer `i`. Whenever `nums[i]` is not equal to `val`, we place it at the `j`th index and increment `j`.
3. The final value of `j` gives the number of elements in `nums` that are not equal to `val`.

### 🖥️ **Code Implementation**

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
       int j = 0; // Pointer to track position for elements that are not val
        for(int i = 0; i < nums.size(); i++) {
            // If nums[i] is not the value to be removed, place it at the next available position (j)
            if(nums[i] != val) {
                nums[j] = nums[i];
                j++; // Move j to the next position
            }
        }
        return j; // Return the count of elements that are not equal to val
    }
};
