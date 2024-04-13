
# Longest Consecutive Sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.
 
```
Example 1:

Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

Example 2:

Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
 
 
```

## Solution 

```java
public int longestConsecutive(int[] nums) {
        if(nums.length==0) return 0;
        HashSet<Integer> hashSet = new HashSet<>();
        int maxSeq = 1;
        for(int n:nums){
            hashSet.add(n);
        }
        for(int num:nums){
            if(!hashSet.contains(num-1)){
                int sum = 1;
                while(hashSet.contains(num+1)){
                    num++;
                    sum++;
                }
                maxSeq = Math.max(maxSeq, sum);
            }  
        } 
        return maxSeq; 
    }
```

#### Space complexity : O(n)
#### Time complexity: O(n)
