
# Permutations

### Problem Link 
##### https://leetcode.com/problems/permutations/description/
### Description
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.
```
Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
Example 2:

Input: nums = [0,1]
Output: [[0,1],[1,0]]
Example 3:

Input: nums = [1]
Output: [[1]]
 
```

## Solution 
### My Solution

```java
class Solution {
    List<List<Integer>> permutation = new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        helper(nums,0);
        return permutation;
    }

    public void helper(int[] nums, int pos){
        if(pos==nums.length-1){
            List<Integer> smallList = new ArrayList<>();
            for(int i:nums){
                smallList.add(i);
            }
            permutation.add(smallList);
            return;
        }
        for(int i=pos;i<nums.length;i++){
            swap(nums,i,pos);
            helper(nums,pos+1);
            swap(nums,i,pos);
        }
    }

    public void swap(int[] nums, int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
### Neet Solution

```java

import java.util.ArrayList;
import java.util.Arrays;

class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        function(ans, nums, 0);
        return ans;
    }

    public void function(List<List<Integer>> ans, int[] arr, int start) {
        if (start == arr.length) {
            List<Integer> list = new ArrayList();
            for (int i = 0; i < arr.length; i++) list.add(arr[i]);
            ans.add(list);
            return;
        }

        for (int i = start; i < arr.length; i++) {
            swap(arr, start, i);
            function(ans, arr, start + 1);
            swap(arr, start, i);
        }
    }

    public void swap(int[] arr, int a, int b) {
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
}


```