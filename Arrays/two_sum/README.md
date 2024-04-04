
# Two Sum

## Problem Link
https://leetcode.com/problems/two-sum/description/

## Description
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Examples 
```
Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
```

## Solutions

### Brute Force 
```java
 public int[] bruteForce(int[] nums, int target){
        int[] result = new int[2];
        int n = nums.length;
        for(int i=0;i<n-1;i++){
            for(int j=i+1;j<n;j++){
                if(nums[i]+nums[j]==target){
                    result[0]=i;
                    result[1]=j;
                    return result;
                }
            }
        } 
        return result;
    }
```

#### Time Complexity: O(n^2)
#### Space Complexity: O(1) 

### Using DataStructure

```java
public int[] dsSolution(int[] nums, int target){
        int n = nums.length;
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<n;i++){
            map.put(nums[i],i);
        }

        for(int i=0;i<n;i++){
            int second = target - nums[i];
            if(map.containsKey(second) && i!=map.get(second)){
                return new int[] {i,map.get(second)};
            }
        }
        return null;
    }
```
#### Time Complexity: O(n)
#### Space Complexity: O(n)