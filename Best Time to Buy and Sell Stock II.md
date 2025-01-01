# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
In this repository, I share my daily solutions to LeetCode problems. Each solution includes well-commented code and detailed explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or an experienced coder, this repository is designed to inspire learning and improve problem-solving skills.

> **Daily Challenge** 💪: One problem, every single day! 🚀

---

## 🚀 Problem: [**122. Best Time to Buy and Sell Stock II**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

### 📝 **Problem Description**

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `i-th` day.

On each day, you may decide to buy and/or sell the stock.  
You can only hold at most one share of the stock at any time.  
However, you can buy it and immediately sell it on the same day.

Return the **maximum profit** you can achieve.

---

### 🏆 **Example Test Cases**

#### Example 1:

**Input:**  
`prices = [7,1,5,3,6,4]`

**Output:**  
`7`

**Explanation:**  
Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = `5-1 = 4`.  
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = `6-3 = 3`.  
Total profit is `4 + 3 = 7`.

---

#### Example 2:

**Input:**  
`prices = [1,2,3,4,5]`

**Output:**  
`4`

**Explanation:**  
Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = `5-1 = 4`.  
Total profit is `4`.

---

#### Example 3:

**Input:**  
`prices = [7,6,4,3,1]`

**Output:**  
`0`

**Explanation:**  
There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of `0`.

---

### 💡 **Solution Explanation**

The goal is to maximize profit by summing up all profitable consecutive price differences. If the price on day `i` is greater than on day `i-1`, then selling on day `i` is profitable. 

We simulate this by summing up all positive differences in the array.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>

class Solution {
public:
    int maxProfit(std::vector<int>& prices) {
        int sum = 0;          // Total profit
        int s = prices[0];    // Track the previous price

        for(int i = 0; i < prices.size(); i++) {
            if(s < prices[i]) {
                // Add profit when today's price is greater than yesterday's price
                sum += prices[i] - s;
            }
            // Update the previous price to today's price
            s = prices[i];
        }
        return sum;  // Return the total profit
    }
};
