# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
In this repository, I share my daily solutions to LeetCode problems. Each solution includes well-commented code and detailed explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or an experienced coder, this repository is designed to inspire learning and improve problem-solving skills.

> **Daily Challenge** 💪: One problem, one solution, every single day! 🚀

---

## 🚀 Problem: [**80. Remove Duplicates from Sorted Array II**](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

### 📝 **Problem Description**

Given an integer array `nums` sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result placed in the first part of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.

You need to return `k` after placing the final result in the first `k` slots of `nums`.

**Note**:
- Do not allocate extra space for another array.
- Modify the input array in-place with O(1) extra memory.

### 🏆 **Example Test Cases**

#### Example 1:

**Input:**  
`nums = [1, 1, 1, 2, 2, 3]`

**Output:**  
`5, nums = [1, 1, 2, 2, 3, _]`

**Explanation:**  
The function returns `k = 5`, with the first five elements of `nums` being `[1, 1, 2, 2, 3]`. The remaining elements are not important and can be anything.

#### Example 2:

**Input:**  
`nums = [0, 0, 1, 1, 1, 1, 2, 3, 3]`

**Output:**  
`7, nums = [0, 0, 1, 1, 2, 3, 3, _, _]`

**Explanation:**  
The function returns `k = 7`, with the first seven elements of `nums` being `[0, 0, 1, 1, 2, 3, 3]`. The remaining elements are not important.

---

### 💡 **Solution Explanation**

This problem can be solved using the **two-pointer technique**. We maintain a pointer `h` that will indicate where the next valid element should be placed in the array. We iterate through the array, comparing each element with the element two places before it. If the current element is different, we place it at the `h`-th position and move `h` forward. This ensures that no element appears more than twice in the array. The final value of `h` will give the count of unique elements in the array.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>

class Solution {
public:
    int removeDuplicates(std::vector<int>& nums) {
        int h = 2;  // Pointer for placing valid elements
        int n = nums.size();
        
        // If the length of nums is 2 or less, return n
        if (n <= 2) return n;
        
        // Iterate from the 3rd element (index 2) to the end
        for (int i = 2; i < n; i++) {
            // Check if the current element is different from the element two places before it
            if (nums[i] != nums[h - 2]) {
                // Place the element at the h-th position
                nums[h] = nums[i];
                h++;  // Move the pointer forward
            }
        }
        
        // Return the number of valid elements
        return h;
    }
};
