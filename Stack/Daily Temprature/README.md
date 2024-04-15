
# Daily Temperatures 

### Problem Link 
##### https://leetcode.com/problems/daily-temperatures/description/

### Description
Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.
 
```
Example 1:

Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
Example 2:

Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
Example 3:

Input: temperatures = [30,60,90]
Output: [1,1,0]
```

## Solution 

### Brute Force
```java
private int[] bruteForce(int[] temperatures) {
        int n = temperatures.length,sum;
        int[] result = new int[n];
        for(int i=0;i<n;i++){
            sum = 1;
            for(int j=i+1;j<n;j++){
                if(temperatures[i]>temperatures[j]){
                    sum++;
                }
                else{
                    result[i] = sum;
                    break;
                }
            }
        }
        return result;
    }
```

### Using Stack
```java
private int[] Optimised(int[] temperatures) {
        Stack<Integer> stack = new Stack<>();
        int n = temperatures.length;
        int[] result = new int[n];
        for(int currDay = 0;currDay<n;currDay++){
            while(!stack.isEmpty() && temperatures[currDay]>temperatures[stack.peek()]){
                int prevDay = stack.pop();
                result[prevDay] = currDay - prevDay;
            }
            stack.push(currDay);
        }
        return result;
    }
```

### Using Better Algorithm
```java
public int[] dailyTemperatures(int[] temperatures) {
        
        if (temperatures == null || temperatures.length < 1) {
            return new int[] {};
        }

        int[] results = new int[temperatures.length];
        int maxTempSoFar = Integer.MIN_VALUE;

        for (int i = temperatures.length - 1; i >= 0; i--) {
            int currentTemp = temperatures[i];

            if (currentTemp >= maxTempSoFar) {
                maxTempSoFar = currentTemp;
                continue;
            }

            int days = 1;


            while (temperatures[i + days] <= currentTemp) {
                days += results[i + days];
            }
            results[i] = days;
        }
        return results;
    }
```


