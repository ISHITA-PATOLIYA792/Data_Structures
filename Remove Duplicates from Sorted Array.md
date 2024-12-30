# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
Here, I share my daily solutions to LeetCode problems, with well-commented code and explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or experienced, this repo is meant to inspire learning and problem-solving.

> **Daily Coding Practice** 💪: Sharpen your skills with a new challenge every single day! 🚀

---

## 🚀 Problem: [**26. Remove Duplicates from Sorted Array**](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

### 📝 **Problem Description**

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in `nums`.

Consider the number of unique elements of `nums` to be `k`. To get accepted, you need to do the following:

1. Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
2. Return `k`.

---

### 🏆 **Example Test Cases**

#### Example 1:
**Input:**  
`nums = [1, 1, 2]`  
**Output:**  
`2, nums = [1, 2, _]`  
**Explanation:**  
Your function should return `k = 2`, with the first two elements of `nums` being `1` and `2` respectively. It does not matter what you leave beyond the returned `k` (hence they are underscores).

#### Example 2:
**Input:**  
`nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]`  
**Output:**  
`5, nums = [0, 1, 2, 3, 4, _, _, _, _, _]`  
**Explanation:**  
Your function should return `k = 5`, with the first five elements of `nums` being `0`, `1`, `2`, `3`, and `4` respectively. It does not matter what you leave beyond the returned `k` (hence they are underscores).

---

### 💡 **Solution Explanation**

The problem is solved using a **two-pointer** approach:
- We initialize a pointer `h` to track the position of the next unique element.
- We iterate through the array starting from the second element (`i = 1`).
- If the current element `nums[i]` is different from the previous element `nums[i-1]`, it means it's a unique element, so we place it at position `h` and increment `h`.
- At the end of the iteration, `h` will contain the count of unique elements, and the first `h` elements in `nums` will be the unique elements.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        // Initialize 'h' to 1 because the first element is always considered unique
        int h = 1;
        
        // Start iterating from the second element (i = 1)
        for (int i = 1; i < nums.size(); i++) {
            // Check if the current element is different from the previous one
            if (nums[i] != nums[i - 1]) {
                // If it's a unique element, place it at the 'h' position
                nums[h] = nums[i];
                // Increment 'h' to move to the next position for potential unique element
                h++;
            }
        }
        
        // Return 'h' as the count of unique elements in the array
        return h;
    }
};

