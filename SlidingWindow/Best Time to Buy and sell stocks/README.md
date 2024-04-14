
# Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
 
```
Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

Example 2:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

## Solution 
### Brute Force

##### Brute force solution would use two loops and to calculate all the profit and choose the max one with time complexity O(n^2)

### My Solution
```java
public int maxProfit(int[] prices) {
        int lmin=prices[0];
        int lmax = 0;
        for(int i=1;i<prices.length;i++){
            if(prices[i]-prices[i-1]<0){
                lmin = Math.min(lmin,prices[i]);
            }
            lmax = Math.max(lmax,prices[i]-lmin);
        }
        return lmax;
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n)

### Sliding window solution

```java
public int maxProfit(int[] prices) {
        int left = 0;
        int right = 1;
        int maxProfit = 0;
        while (right < prices.length) {
            if (prices[left] < prices[right]) {
                maxProfit = Math.max(maxProfit, prices[right] - prices[left]);
            } else {
                left = right;
            }
            right++;
        }
        return maxProfit;
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n)
