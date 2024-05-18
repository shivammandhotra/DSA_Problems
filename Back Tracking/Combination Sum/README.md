
# Combination Sum

### Problem Link 
##### https://leetcode.com/problems/combination-sum/description/
### Description
Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the 
frequency
 of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.
```
Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]
Example 3:

Input: candidates = [2], target = 1
Output: []
 
```

## Solution 
### My Solution

```java
class Solution {

    List<List<Integer>> combination = new ArrayList<>();
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        helper(candidates,target,new ArrayList<>(),0,0);
        return combination;
    }

    public void helper(int[] nums, int tar, List<Integer> sList, int sum, int pos){
        if(sum>tar){
            return;
        }
        if(tar==sum){
            combination.add(new LinkedList<>(sList));
            return;
        }
        for(int i=pos;i<nums.length;i++){
            sum += nums[i];
            sList.add(nums[i]);
            helper(nums,tar,sList,sum,pos);
            sum -= nums[i];
            sList.remove(sList.size()-1);
            pos++;
        }

    }
}
```
### Neet Solution

```java

class Solution {

    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        List<Integer> cur = new ArrayList();
        backtrack(candidates, target, ans, cur, 0);
        return ans;
    }

    public void backtrack(
        int[] candidates,
        int target,
        List<List<Integer>> ans,
        List<Integer> cur,
        int index
    ) {
        if (target == 0) {
            ans.add(new ArrayList(cur));
        } else if (target < 0 || index >= candidates.length) {
            return;
        } else {
            cur.add(candidates[index]);
            backtrack(candidates, target - candidates[index], ans, cur, index);

            cur.remove(cur.get(cur.size() - 1));
            backtrack(candidates, target, ans, cur, index + 1);
        }
    }
}


```