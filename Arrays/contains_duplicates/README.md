
# Contains Duplicate

## Problem Link
https://leetcode.com/problems/contains-duplicate/description/

## Description
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

## Examples 
```
Example 1:
Input: nums = [1,2,3,1]
Output: true

Example 2:
Input: nums = [1,2,3,4]
Output: false

Example 3:
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Solutions

### Brute Force 
```java
 public boolean bruteForce(int[] nums){
        int n = nums.length;
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                if(nums[i]==nums[j]){
                    return true;
                }
            }
        }
        return false;
    }
```

#### Time Complexity: O(n^2)
#### Space Complexity: O(1) 

### Algorithmic Approach
```java
public boolean algoSolution(int[] nums){
        int n = nums.length;
        Arrays.sort(nums);
        for(int i=0;i<n-1;i++){
            if(nums[i]==nums[i+1]){
                return true;
            }
        }
        return false;
    }
```
#### Time Complexity: O(nlogn)
#### Space Complexity: O(1) 

### Using DataStructure

```java
public boolean dataStructure(int[] nums){
        int n = nums.length;
        HashSet<Integer> hashSet = new HashSet<>();
        for(int i=0;i<n;i++){
            if(hashSet.contains(nums[i])){
                return true;
            }
            hashSet.add(nums[i]);
        }
        return false;
    }
```
#### Time Complexity: O(n)
#### Space Complexity: O(n)