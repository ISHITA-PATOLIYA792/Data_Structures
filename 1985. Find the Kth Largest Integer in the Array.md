# 1985. Find the Kth Largest Integer in the Array

## Problem Description

You are given an array of strings nums and an integer k. Each string in nums represents an integer without leading zeros.

Return the string that represents the k-th largest integer in nums.

*Note:* Duplicate numbers should be counted distinctly. For example, if nums is ["1","2","2"], "2" is the first largest integer, "2" is the second-largest integer, and "1" is the third-largest integer.

### Examples

#### Example 1
plaintext
Input: nums = ["3","6","7","10"], k = 4
Output: "3"
Explanation:
The numbers in nums sorted in non-decreasing order are ["3","6","7","10"].
The 4th largest integer in nums is "3".


#### Example 2
plaintext
Input: nums = ["2","21","12","1"], k = 3
Output: "2"
Explanation:
The numbers in nums sorted in non-decreasing order are ["1","2","12","21"].
The 3rd largest integer in nums is "2".


#### Example 3
plaintext
Input: nums = ["0","0"], k = 2
Output: "0"
Explanation:
The numbers in nums sorted in non-decreasing order are ["0","0"].
The 2nd largest integer in nums is "0".


---

## Constraints

- 1 <= k <= nums.length <= 10^4
- 1 <= nums[i].length <= 100
- nums[i] consists of only digits.
- nums[i] does not have leading zeros except for the zero itself.

---

## Solution

Here is the Python solution that sorts the array based on the integer values of the strings and retrieves the k-th largest integer:

### Python Code
python
from typing import List

class Solution:
    def kthLargestNumber(self, nums: List[str], k: int) -> str:
        # Sort the numbers by their integer values in ascending order
        nums.sort(key=int)
        # Return the k-th largest element
        return nums[-k]


### Explanation of the Code
1. *Sorting*: The nums list is sorted using the sort() method with a custom key, int. This ensures that the strings are sorted based on their numerical value, not lexicographical order.
2. *Retrieve k-th Largest*: The k-th largest element is accessed using negative indexing (nums[-k]). Negative indexing starts counting from the end of the list, making it efficient to access the k-th largest element.

### Complexity Analysis
- *Time Complexity*: Sorting the list takes O(n log n) where n is the length of nums.
- *Space Complexity*: O(1) additional space is used for sorting, as it is done in-place.

---

## Example Execution

### Example Input
python
nums = ["3","6","7","10"]
k = 4


### Example Output
python
"3"


---

## Usage
To use the solution, create an instance of the Solution class and call the kthLargestNumber method with appropriate arguments:

python
solution = Solution()
result = solution.kthLargestNumber(["3","6","7","10"], 4)
print(result)  # Output: "3"
