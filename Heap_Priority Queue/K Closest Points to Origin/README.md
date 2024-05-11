
# K Closest Points to Origin

### Problem Link 
##### https://leetcode.com/problems/k-closest-points-to-origin/description/
### Description
Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane and an integer k, return the k closest points to the origin (0, 0).

The distance between two points on the X-Y plane is the Euclidean distance (i.e., √(x1 - x2)2 + (y1 - y2)2).

You may return the answer in any order. The answer is guaranteed to be unique (except for the order that it is in).
```
Example 1:


Input: points = [[1,3],[-2,2]], k = 1
Output: [[-2,2]]
Explanation:
The distance between (1, 3) and the origin is sqrt(10).
The distance between (-2, 2) and the origin is sqrt(8).
Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.
We only want the closest k = 1 points from the origin, so the answer is just [[-2,2]].
Example 2:

Input: points = [[3,3],[5,-1],[-2,4]], k = 2
Output: [[3,3],[-2,4]]
Explanation: The answer [[-2,4],[3,3]] would also be accepted.
 
```

## Solution 
### My Solution

```java
public int[][] kClosest(int[][] points, int k) {
        Comparator<Pair<Integer, Integer>> comparator = Comparator.comparing(Pair::getKey);
        PriorityQueue<Pair<Integer,Integer>> queue = new PriorityQueue<>(comparator);
        for(int i=0;i<points.length;i++){
            int x = points[i][0];
            int y = points[i][1];
            int z = (x*x) + (y*y);
            Pair<Integer,Integer> pair = new Pair<>(z,i);
            queue.offer(pair);
        }
        int[][] Kclosests = new int[k][2];
        for(int i=0;i<k;i++){
            int l = queue.poll().getValue();
            Kclosests[i][0] = points[l][0];
            Kclosests[i][1] = points[l][1];
        }
        return Kclosests;
    }
```

### Neety Solution

```java
//First solution Time Complexity is O(NlogN)
//Just take a min heap and add the values using the formula and return the top k values
//We can completely ignore the square root as we are just comparing the values (if a*a>b*b => a>b)

class Solution {

    public int[][] kClosest(int[][] points, int k) {
        PriorityQueue<int[]> q = new PriorityQueue<>((a, b) ->
            Integer.compare(
                (a[0] * a[0] + a[1] * a[1]),
                (b[0] * b[0] + b[1] * b[1])
            )
        );
        for (int[] point : points) {
            q.add(point);
        }
        int[][] ans = new int[k][2];
        for (int i = 0; i < k; i++) {
            int[] cur = q.poll();
            ans[i][0] = cur[0];
            ans[i][1] = cur[1];
        }
        return ans;
    }
}

//This approach is a sightly optimized approach here we can use a max heap and maintain its size as k.
//So when we do the removal the time complexity will reduce from logn to logk
//Max heap because we will remove the top elements (the one which are greater)
//Overall Time complexity O(NlogK)

class Solution {

    public int[][] kClosest(int[][] points, int k) {
        PriorityQueue<int[]> q = new PriorityQueue<>((a, b) ->
            Integer.compare(
                (b[0] * b[0] + b[1] * b[1]),
                (a[0] * a[0] + a[1] * a[1])
            )
        ); //only this is changed (swapped)
        for (int[] point : points) {
            q.add(point);
            //remove when size increase k
            if (q.size() > k) {
                q.remove();
            }
        }
        int[][] ans = new int[k][2];
        for (int i = 0; i < k; i++) {
            int[] cur = q.poll();
            ans[i][0] = cur[0];
            ans[i][1] = cur[1];
        }
        return ans;
    }
}
//There are also some O(N) solutions using quick select and binary search https://leetcode.com/problems/k-closest-points-to-origin/solution/

```


