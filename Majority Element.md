# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
In this repository, I share my daily solutions to LeetCode problems. Each solution includes well-commented code and detailed explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or an experienced coder, this repository is designed to inspire learning and improve problem-solving skills.

> **Daily Challenge** 💪: One problem, every single day! 🚀

---

## 🚀 Problem: [**169. Majority Element**](https://leetcode.com/problems/majority-element/)

### 📝 **Problem Description**

Given an array `nums` of size `n`, return the majority element.

The **majority element** is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

---

### 🏆 **Example Test Cases**

#### Example 1:

**Input:**  
`nums = [3, 2, 3]`

**Output:**  
`3`

#### Example 2:

**Input:**  
`nums = [2, 2, 1, 1, 1, 2, 2]`

**Output:**  
`2`

---

### 💡 **Solution Explanation**

This solution uses a **hashmap (or dictionary)** to count the occurrences of each element in the array. After counting the occurrences, the solution iterates through the hashmap to find the element that appears more than `⌊n / 2⌋` times, which is returned as the majority element.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>
#include <map>

class Solution {
public:
    int majorityElement(std::vector<int>& nums) {
        std::map<int, int> frequencyMap;  // Map to store the frequency of elements

        // Count the occurrences of each element in the array
        for (auto& num : nums) {
            frequencyMap[num]++;
        }

        int majorityThreshold = nums.size() / 2;  // Calculate the majority threshold
        int majorityElement = 0;  // Variable to store the majority element

        // Find the element with a frequency greater than the majority threshold
        for (auto& entry : frequencyMap) {
            if (entry.second > majorityThreshold) {
                majorityElement = entry.first;  // Store the majority element
                break;  // Exit the loop as we found the majority element
            }
        }

        return majorityElement;  // Return the majority element
    }
};
