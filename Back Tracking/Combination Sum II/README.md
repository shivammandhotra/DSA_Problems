
# Combination Sum II

### Problem Link 
##### https://leetcode.com/problems/combination-sum-ii/description/
### Description
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.
```
Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
Example 2:

Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
 
```

## Solution 


```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        subComb(candidates,0,target,list,ans);
        return ans;
    }

    public void subComb(int[] nums, int idx,int target,List<Integer> list,List<List<Integer>> ans){
        if(target==0){
            ans.add(new ArrayList<>(list));
        }
        else if(target<0) return;
        else{
            for(int i=idx;i<nums.length;i++){
                if(i>idx && nums[i-1]==nums[i]) continue;
                list.add(nums[i]);
                subComb(nums,i+1,target-nums[i],list,ans);
                list.remove(list.size()-1);
            }
        }
    }
}
```
