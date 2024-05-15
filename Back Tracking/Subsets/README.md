
# Subsets

### Problem Link 
##### https://leetcode.com/problems/subsets/description/
### Description
Given an integer array nums of unique elements, return all possible 
subsets
 (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.
```
Example 1:

Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
Example 2:

Input: nums = [0]
Output: [[],[0]]
 
```

## Solution 
### My Solution

```java
List<List<Integer>> badewali = new LinkedList<>();
    public List<List<Integer>> subsets(int[] nums) {
        List<Integer> chotiwali = new LinkedList<>();
        recursion(nums,0,chotiwali);
        return badewali;
    }

    public void recursion(int[] nums,int i,List<Integer> chotiwali){
        if(i>=nums.length){
            badewali.add(new LinkedList<>(chotiwali));
            return;
        }
        recursion(nums,i+1,chotiwali);
        chotiwali.add(nums[i]);
        recursion(nums,i+1,chotiwali);
        chotiwali.remove(chotiwali.size()-1);
        
    }
```
### Neet Solution

```java

// The idea is to have two conditions: 
// One in which we will take the element into consideration, 
// Second in which we won't take the element into consideration.
class Solution {

    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        helper(ans, 0, nums, list);
        return ans;
    }

    public void helper(
        List<List<Integer>> ans,
        int start,
        int[] nums,
        List<Integer> list
    ) {
        if (start >= nums.length) {
            ans.add(new ArrayList<>(list));
        } else {
            // add the element and start the  recursive call
            list.add(nums[start]);
            helper(ans, start + 1, nums, list);
            // remove the element and do the backtracking call.
            list.remove(list.size() - 1);
            helper(ans, start + 1, nums, list);
        }
    }
}


```