
#  Largest Rectangle in Histogram

### Problem Link 
##### https://leetcode.com/problems/largest-rectangle-in-histogram/description/
### Description
Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.
```
Example 1:

Input: heights = [2,1,5,6,2,3]
Output: 10
Explanation: The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.

Example 2:

Input: heights = [2,4]
Output: 4
```

## Solution 
#### See https://www.youtube.com/watch?v=lJLcqDsmYfg for reference
```java
private static int[] prevSmallerElements(int[] heights) {
        // TODO Auto-generated method stub
        int n = heights.length;
        int[] res = new int[n];
        Stack<Integer> stack = new Stack<>();

        stack.push(-1);

        for(int i=0;i<n;i++){
            while(stack.peek()!=-1 && heights[stack.peek()]>=heights[i]){
                stack.pop();
            }
            res[i] = stack.peek();
            stack.push(i);
        }
        return res;
    }

    private static int[] nextSmallerElements(int[] heights) {
        // TODO Auto-generated method stub
        int n = heights.length;
        int[] res = new int[n];
        Stack<Integer> stack = new Stack<>();

        stack.push(-1);

        for(int i=n-1;i>=0;i--){
            while(stack.peek()!=-1 && heights[stack.peek()]>=heights[i]){
                stack.pop();
            }
            res[i] = stack.peek();
            stack.push(i);
        }
        return res;
    }

    public int largestRectangleArea(int[] heights) {
        int n = heights.length;
     
        int[] next = nextSmallerElements(heights);
        int[] prev = prevSmallerElements(heights);

        int area = Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
            int l = heights[i];
            if(next[i]==-1) next[i] = n;
            int b = next[i] - prev[i] -1;
            int newArea = l*b;
            area = Math.max(area,newArea );
        }
        return area;
    }
}
```



