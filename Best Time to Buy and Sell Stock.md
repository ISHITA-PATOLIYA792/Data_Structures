# 🎉 **LeetCode Daily Solutions** 📅

Welcome to my **LeetCode Daily Solutions** repository!  
In this repository, I share my daily solutions to LeetCode problems. Each solution includes well-commented code and detailed explanations to help you understand the approach and logic behind each solution. Whether you're a beginner or an experienced coder, this repository is designed to inspire learning and improve problem-solving skills.

> **Daily Challenge** 💪: One problem,every single day! 🚀

---

## 🚀 Problem: [**121. Best Time to Buy and Sell Stock**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

### 📝 **Problem Description**

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i-th` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.

---

### 🏆 **Example Test Cases**

#### Example 1:

**Input:**  
`prices = [7,1,5,3,6,4]`

**Output:**  
`5`

**Explanation:**  
Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = `6-1 = 5`.  
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

#### Example 2:

**Input:**  
`prices = [7,6,4,3,1]`

**Output:**  
`0`

**Explanation:**  
In this case, no transactions are done, and the maximum profit is `0`.

---

### 💡 **Solution Explanation**

The goal is to find the maximum profit by identifying the lowest stock price to buy and the highest stock price to sell after buying. This is achieved in a single traversal of the array.

---

### 👨‍💻 **Solution Code (C++)**

```cpp
#include <vector>
#include <climits>

class Solution {
public:
    int maxProfit(std::vector<int>& prices) {
        int lsf = INT_MAX;  // Least so far: the minimum price encountered so far
        int op = 0;         // Overall profit: the maximum profit observed so far
        int pist = 0;       // Profit if sold today: the profit from selling on the current day

        for(int i = 0; i < prices.size(); i++){
            // Update the least so far if the current price is lower
            if(prices[i] < lsf){
                lsf = prices[i];
            }
            // Calculate the profit if sold today
            pist = prices[i] - lsf;
            // Update the overall profit if the current profit is greater
            if(op < pist){
                op = pist;
            }
        }
        return op;  // Return the maximum profit
    }
};
