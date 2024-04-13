
# Trapping Rain Water

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.
 
```
Example 1:


Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
Example 2:

Input: height = [4,2,0,3,2,5]
Output: 9
 
 
```

## Solution 
### Using Arrays

```java
public int trap(int[] height) {
        int n = height.length;
        int[] lftMxBndry = new int[n];
        int[] rtMxBndry = new int[n];
        int minOfRaL;
        int sum = 0;
        // calculateing  left max boundary.
        lftMxBndry[0] = height[0];
        for(int i =1;i<n;i++){
            lftMxBndry[i] = Math.max(lftMxBndry[i-1], height[i]);
        }
        // calculating right max boundary.
        rtMxBndry[n-1] = height[n-1];
        for(int i=n-2;i>=0;i--){
            rtMxBndry[i] = Math.max(rtMxBndry[i+1], height[i]);
        }
        // calculation total traped water.
        for(int i=1;i<n-1;i++){
            minOfRaL = Math.min(rtMxBndry[i],lftMxBndry[i]);
            sum += (minOfRaL - height[i])>0?(minOfRaL - height[i]):0;
        }
        return sum;
    }
```

#### Space complexity : O(n)
#### Time complexity: O(n)

### Using Twopointers

```java

public int trap(int[] heights) {
    if (heights.length == 0) return 0;

    int l = 0, r = heights.length - 1;
    int leftMax = heights[l], rightMax = heights[r];
    int res = 0;

     while (l < r) {
        if (leftMax < rightMax) {
            l++;
            leftMax = Math.max(leftMax, heights[l]);
            res += leftMax - heights[l];
        } else {
            r--;
            rightMax = Math.max(rightMax, heights[r]);
            res += rightMax - heights[r];
        }
    }

    return res;
}
```

#### Space complexity : O(1)
#### Time complexity: O(n)





