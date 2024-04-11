
# 3Sum

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

 
```
Example 1:

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

Example 2:

Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.

Example 3:

Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
 
 
```

## Solution 
### Brute Force

```java
public static List<List<Integer>> bruteForce(int[] nums){
        int n = nums.length;

        List<List<Integer>> Results = new ArrayList<>();

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                for(int k=0;k<n;k++){
                    if(i!=j && j!=k && i!=k && nums[i]+nums[j]+nums[k]==0){
                        List<Integer> newList = new ArrayList<>();
                        newList.add(nums[i]);
                        newList.add(nums[j]);
                        newList.add(nums[k]);
                        Collections.sort(newList);
                        if(Results.contains(newList)){
                            continue;
                        }
                        Results.add(newList);
                    }
                }
            }
        }
        return Results;
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n^3)

### Using DataStructure

```java
public static List<List<Integer>> aBitOptimized(int[] nums){
        int n = nums.length;
        List<List<Integer>> results = new ArrayList<>();
        HashSet<Integer> hashSet = new HashSet<>();

        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                List<Integer> list = new ArrayList<>();
                int k = -(nums[i]+nums[j]);
                if(hashSet.contains(k)){
                    list.add(nums[i]);
                    list.add(nums[j]);
                    list.add(k);
                    Collections.sort(list);
                    if(!results.contains(list)){
                        results.add(list);
                    }
                }
                hashSet.add(nums[j]);
            }
            hashSet = new HashSet();
        }
        return results;
    }
```

#### Space complexity : O(n)
#### Time complexity: O(n^2)


### Using two Pointers approach

```java
public static List<List<Integer>> mostOptimizedApproach(int [] nums){
        List<List<Integer>> arrayList = new ArrayList<>();
        int n = nums.length;
        Arrays.sort(nums);
        for(int i=0;i<n;i++){
            if(i>0 && nums[i-1]==nums[i]) continue;
            int j=i+1;
            int k=n-1;

            while(j<k){
                int sum = nums[i]+nums[j]+nums[k];
                if(sum<0){
                    j++;
                }
                else if(sum>0){
                    k--;
                }
                else{
                    List<Integer> list = new ArrayList(3);
                    list.add(nums[i]);
                    list.add(nums[j]);
                    list.add(nums[k]);
                    arrayList.add(list);
                    j++;
                    k--;
                    while(j<k && nums[j]==nums[j-1]) j++;
                    while(j<k && nums[k]==nums[k+1]) k--;  
                }
            }
        }
        return arrayList;
    }
```

#### Space complexity : O(n)
#### Time complexity: O(nlogn)



