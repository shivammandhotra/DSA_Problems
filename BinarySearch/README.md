
# Binary Search

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.
 
```
Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

## Solution 

### My Solution
```java
class Solution {
    public int search(int[] nums, int target) {
        return binary(nums,0,nums.length-1,target);
    }

    public int binary(int[] nums,int start, int end, int target){
        if(start>end) return -1;
        int mid = start-(start-end)/2;
        if(nums[mid]==target)
        {
            return mid;
        }
        else if(nums[mid] > target){
            return binary(nums,start,mid-1,target);
        }
        else{
            return binary(nums,mid+1,end,target);
        }
    }
}
```



