
# Search a 2D Matrix

### Problem Link 
##### https://leetcode.com/problems/search-a-2d-matrix/description/

### Description
You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.
 
```
Example 1:


Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true

Example 2:


Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
```

## Solution 

### APPROACH 1
```java
public boolean searchMatrix1(int[][] matrix, int target) {
        int i = 0;
        int j = matrix[0].length-1;

        while(i<matrix.length && j>=0){
            if(matrix[i][j]==target){
                return true;
            }
            else if(matrix[i][j]<target){
                i++;
            }
            else{
                j--;
            }
        }
        return false;
    }
```

### APPROACH 2
```java
public boolean searchMatrix2(int[][] matrix, int target) {
        int rows = matrix.length;
        int cols = matrix[0].length;

        int low = 0;
        int high = rows*cols;

        while(low<high){
            int mid = (low+high)/2;

            if(matrix[mid/cols][mid%cols]==target){
                return true;
            }
            else if(matrix[mid/cols][mid%cols]<target){
                low = mid+1;
            }
            else{
                high = mid;
            }
        }
        return false;
    }
```
