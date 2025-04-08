
---

## Solution Approach 💡

- Traverse the array from the end.
- Use a hash map (`unordered_map`) to track the frequency of elements.
- If any duplicate element is found while traversing:
  - Calculate how many operations are required to remove up to that index.
  - Operation Count = `(i / 3) + 1`
- If no duplicates are found → Return 0.

---

## Code Implementation 💻

```cpp
class Solution {
public:
    int minimumOperations(vector<int>& nums) {
        int n = nums.size();
        unordered_map<int, int> mp;
        
        for (int i = n - 1; i >= 0; i--) {
            if (mp.find(nums[i]) != mp.end()) {
                return i / 3 + 1;
            }
            mp[nums[i]]++;
        }
        return 0;
    }
};
