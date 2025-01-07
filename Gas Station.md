# 🚗 [134. Gas Station](https://leetcode.com/problems/gas-station/)

## 📜 Problem Statement

There are `n` gas stations along a circular route. Each station provides a certain amount of gas (`gas[i]`), and it costs a certain amount (`cost[i]`) to travel to the next station.  

Your car has an unlimited gas tank, and you start the journey with an empty tank at one of the gas stations.  

**Task**: Return the starting gas station's index if you can complete the circuit once in the clockwise direction. Otherwise, return `-1`.  

It is guaranteed that if a solution exists, it is unique.

---

### 🔍 Examples

#### Example 1:
**Input:**  
`gas = [1,2,3,4,5]`  
`cost = [3,4,5,1,2]`  
**Output:**  
`3`  

**Explanation:**  
- Start at station 3 (`gas[3] = 4`): `Tank = 0 + 4 = 4`  
- Travel to station 4: `Tank = 4 - 1 + 5 = 8`  
- Travel to station 0: `Tank = 8 - 2 + 1 = 7`  
- Travel to station 1: `Tank = 7 - 3 + 2 = 6`  
- Travel to station 2: `Tank = 6 - 4 + 3 = 5`  
- Travel back to station 3: `Tank = 5 - 5 = 0`  

Thus, starting at station 3 allows completing the circuit.

#### Example 2:
**Input:**  
`gas = [2,3,4]`  
`cost = [3,4,3]`  
**Output:**  
`-1`  

**Explanation:**  
- Starting at any station results in insufficient gas to complete the circuit.

---

## 💡 Approach

The problem is solved using **Greedy Algorithm**:

1. **Key Observations**:
   - To complete the circuit, the total gas available (`total_gas`) must be greater than or equal to the total cost (`total_cost`).
   - If the car cannot reach station `i+1` from station `i`, then station `i+1` becomes the new starting point.
   
2. **Algorithm Steps**:
   - Traverse through all stations while maintaining:
     - `total_gas` and `total_cost` for global feasibility.
     - `curr_gas` to track the gas in the tank for the current segment.
   - If `curr_gas < 0`, reset the starting station and `curr_gas`.

3. **Return**:
   - If `total_gas < total_cost`, return `-1` (circuit completion is impossible).
   - Otherwise, return the `starting` index.

---

## 👨‍💻 Code Implementation (C++)

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int n = gas.size();
        int total_gas = 0, total_cost = 0;
        int curr_gas = 0, starting = 0;

        for (int i = 0; i < n; i++) {
            total_gas += gas[i];
            total_cost += cost[i];
            curr_gas += gas[i] - cost[i];

            if (curr_gas < 0) {
                starting = i + 1; // Reset starting station
                curr_gas = 0;    // Reset current gas
            }
        }

        return (total_gas < total_cost) ? -1 : starting;
    }
};
