# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
Here, I share my daily solutions to LeetCode problems, with well-commented code and explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or experienced, this repo is meant to inspire learning and problem-solving.

> **Daily Coding Practice** 💪: Sharpen your skills with a new challenge every single day! 🚀

---

## 🚀 Problem: [**88. Merge Sorted Array**](https://leetcode.com/problems/merge-sorted-array/)

### 📝 **Problem Description**

You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

Your task is to merge `nums1` and `nums2` into a single array sorted in non-decreasing order. The result should be stored inside `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0`.

---

### 🏆 **Example Test Cases**

#### Example 1:
**Input:**  
`nums1 = [1, 2, 3, 0, 0, 0]`, `m = 3`, `nums2 = [2, 5, 6]`, `n = 3`  
**Output:**  
`[1, 2, 2, 3, 5, 6]`  
**Explanation:**  
The arrays `[1, 2, 3]` and `[2, 5, 6]` are merged to form `[1, 2, 2, 3, 5, 6]`.

#### Example 2:
**Input:**  
`nums1 = [1]`, `m = 1`, `nums2 = []`, `n = 0`  
**Output:**  
`[1]`  
**Explanation:**  
`nums1` remains `[1]` as `nums2` is empty.

#### Example 3:
**Input:**  
`nums1 = [0]`, `m = 0`, `nums2 = [1]`, `n = 1`  
**Output:**  
`[1]`  
**Explanation:**  
Since `nums1` has no elements, the result is `[1]` from `nums2`.

---

### 💡 **Solution Explanation**

The problem is solved using a **two-pointer** technique. We maintain two pointers (`l` and `r`) to traverse through both arrays (`nums1` and `nums2`). We compare the elements and add the smaller one to a temporary array. After merging, the array is copied back to `nums1`.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        // Initialize two pointers for nums1 and nums2
        int l = 0; // Pointer for nums1
        int r = 0; // Pointer for nums2

        // Temporary vector to store the merged elements
        vector<int> temp;

        // Compare elements from nums1 and nums2 and merge them
        while (l < m && r < n) {
            if (nums1[l] <= nums2[r]) {
                temp.push_back(nums1[l]); // Add nums1 element to temp
                l++;
            } else {
                temp.push_back(nums2[r]); // Add nums2 element to temp
                r++;
            }
        }

        // Add remaining elements from nums1 (if any)
        while (l < m) {
            temp.push_back(nums1[l]);
            l++;
        }

        // Add remaining elements from nums2 (if any)
        while (r < n) {
            temp.push_back(nums2[r]);
            r++;
        }

        // Copy the merged elements back to nums1
        for (int i = 0; i < m + n; i++) {
            nums1[i] = temp[i];
        }
    }
};
