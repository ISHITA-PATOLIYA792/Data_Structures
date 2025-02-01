# Median of Two Sorted Arrays

## Problem Statement
Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the median of the two sorted arrays.

The overall run-time complexity should be `O(log (m+n))`.

### **Example 1**
```cpp
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

### **Example 2**
```cpp
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

## Approach
- We perform **binary search** on the smaller array to minimize the search space.
- The arrays are **partitioned** such that the left half contains smaller elements than the right half.
- We compute the **median** based on the partitioning.

## Complexity Analysis
- **Time Complexity:** `O(log min(m, n))` (Binary search on the smaller array)
- **Space Complexity:** `O(1)` (Constant extra space)

## Usage
### **Prerequisites**
- C++ compiler (GCC, Clang, or MSVC)
- Basic knowledge of C++ programming

### **Compilation and Execution**
```sh
g++ median_sorted_arrays.cpp -o median
./median
```

## License
This project is open-source and available under the **MIT License**.
#include <vector>
#include <limits>

using namespace std;

class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        // Ensure nums1 is the smaller array
        if (nums1.size() > nums2.size()) {
            return findMedianSortedArrays(nums2, nums1);
        }

        int x = nums1.size();
        int y = nums2.size();
        int low = 0, high = x;

        while (low <= high) {
            int partitionX = (low + high) / 2;
            int partitionY = (x + y + 1) / 2 - partitionX;

            // Handling edge cases
            int maxLeftX = (partitionX == 0) ? INT_MIN : nums1[partitionX - 1];
            int minRightX = (partitionX == x) ? INT_MAX : nums1[partitionX];

            int maxLeftY = (partitionY == 0) ? INT_MIN : nums2[partitionY - 1];
            int minRightY = (partitionY == y) ? INT_MAX : nums2[partitionY];

            // Correct partition found
            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                // If odd total length, return max of left partition
                if ((x + y) % 2 == 1) {
                    return max(maxLeftX, maxLeftY);
                }
                // If even, return the average of the two middle elements
                return (max(maxLeftX, maxLeftY) + min(minRightX, minRightY)) / 2.0;
            }
            // Move left in nums1
            else if (maxLeftX > minRightY) {
                high = partitionX - 1;
            }
            // Move right in nums1
            else {
                low = partitionX + 1;
            }
        }
        
        throw runtime_error("Input arrays are not sorted or valid.");
    }
};

---

### **Author**
Developed by **Ishita Patoliya** 🚀
