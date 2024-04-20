
#  Koko Eating Bananas

### Problem Link 
##### https://leetcode.com/problems/koko-eating-bananas/description/
### Description
Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.
```
Example 1:

Input: piles = [3,6,7,11], h = 8
Output: 4

Example 2:

Input: piles = [30,11,23,4,20], h = 5
Output: 30

Example 3:

Input: piles = [30,11,23,4,20], h = 6
Output: 23
```

## Solution 1

### just being concerned about the time
```java
public int minEatingSpeed(int[] piles, int h) {
        int right=1,left=1;

        for(int pile: piles){
            right = Math.max(right,pile);
        }

        while(left<right){
            int middle = (left+right)/2;
            int hourSpent = 0;

            for(int pile:piles){
                hourSpent += Math.ceil((double)pile/middle);
            }

            if(hourSpent<=h){
                right = middle;
            }
            else{
                left = middle+1;
            }
        }
        return right;

    }
```

