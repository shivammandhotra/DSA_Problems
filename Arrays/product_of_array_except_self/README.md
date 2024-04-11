
# Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

```
Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

## Firstly the brute force approach

```java
public int[] bruteForceSolution(int[] nums){
        int n = nums.length;
        int[] result = new int[n];
        Arrays.fill(result,1);
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i!=j){
                    result[i] *= nums[j];
                }
            }
        }
        return result;
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n^2)

## Optimised Approach

Creating two arrays ->rightProduct and leftProduct

##### rightProduct -> product of all the number towards right 
##### leftProduct -> product of all the number towards left


```java
public int[] firstOptimized(int[] nums){
        int n = nums.length;
        int[] leftProd = new int[n];
        int[] rightProd = new int[n];
        int[] result = new int[n];
        leftProd[0] = 1;
        for(int i=1;i<n;i++){
            leftProd[i] = leftProd[i-1]*nums[i-1];
        }
        rightProd[n-1] = 1;
        for(int i=n-2;i>=0;i--){
            rightProd[i] = rightProd[i+1]*nums[i+1];
        }
        for(int i=0;i<n;i++){
            result[i]=rightProd[i]*leftProd[i];
        }
        return result;
    }
```
#### Space complexity : O(n)
#### Time complexity: O(n)
## Optimised Approach 2
##### using only one variable instead of 2 arrays

```java
public int[] secondOptimized(int[] nums){
        int n = nums.length;
        int[] ans = new int[n];
        ans[0] = 1;
        for(int i=1;i<n;i++){
            ans[i] = ans[i-1]*nums[i-1];
        }
        int rightProd = 1;
        for(int i=n-1;i>=0;i--){
            ans[i] *= rightProd;
            rightProd *= nums[i];
        }
        return ans;
    }
```
#### Space complexity : O(n)
#### Time complexity: O(n)
