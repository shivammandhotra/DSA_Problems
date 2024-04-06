
# Top K Frequent Elements

## Problem Link
https://leetcode.com/problems/top-k-frequent-elements/description/

## Description
Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

## Examples 
```
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
Example 2:

Input: nums = [1], k = 1
Output: [1]
```

### Solution

```java
public int[] topKFrequent(int[] nums, int k) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int num:nums){
            map.put(num, map.getOrDefault(num,0)+1);
        }
        PriorityQueue<Map.Entry<Integer,Integer>> pq = new PriorityQueue<>(
            (a,b) -> b.getValue() - a.getValue()
        );
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            pq.offer(entry);
        }
        int[] array = new int[k];
        for(int i=0;i<k;i++){
            array[i] = pq.poll().getKey();
        }
        return array; 
    }
```
#### Time Complexity: O(n)
#### Space Complexity: O(n)

## Declaration of Priority Queue

```
PriorityQueue<Map.Entry<Integer,Integer>> pq = new PriorityQueue<>(
            (a,b) -> b.getValue() - a.getValue()
        );
```

#### Here we are defining that we need to sort the elements of the priority queue based on the values in Key Value pair of the maps