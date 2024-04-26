
#   Sliding Window Maximum

### Problem Link 
##### https://leetcode.com/problems/sliding-window-maximum/description/
### Description
You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.
```
Example 1:

Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
Example 2:

Input: nums = [1], k = 1
Output: [1]
```

## Solution 
#### For reference https://www.youtube.com/watch?v=CZQGRp93K4k

### Brute Force 
```java
public int[] maxSlidingWindow(int[] nums, int k) {
        int n = nums.length;
        int q = n - k + 1;
        int newArray[] = new int[q];

        for(int i=0;i<q;i++){
            int max = Integer.MIN_VALUE;
            for(int j=i;j<i+k;j++){
                max = Math.max(max, nums[j]);
            }
            newArray[i] = max;
        }
        return newArray;
    }
    // TC -> O(n*k)
    // SC -> O(1)

```

### Using Deque

```java
public int[] maxSlidingWindow(int[] nums, int k) {
        int n = nums.length;
        int newArray[] = new int[n - k + 1];
        int j=0;
        Deque<Integer> quDeque = new LinkedList<>();

        for(int i=0;i<n;i++){
            if(!quDeque.isEmpty() && quDeque.peekFirst()<i-k+1) quDeque.pollFirst();
            while(!quDeque.isEmpty() && nums[i]>nums[quDeque.peekLast()]) quDeque.pollLast();
            quDeque.offer(i);
            if(i>=k-1){
                newArray[j++] = nums[quDeque.peekFirst()];
            }
        }
        return newArray;
    }
    //TC -> O(n)
    //SC -> O(1)
```



