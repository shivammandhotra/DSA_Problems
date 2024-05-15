
# Task Scheduler

### Problem Link 
##### https://leetcode.com/problems/task-scheduler/description/
### Description
You are given an array of CPU tasks, each represented by letters A to Z, and a cooling time, n. Each cycle or interval allows the completion of one task. Tasks can be completed in any order, but there's a constraint: identical tasks must be separated by at least n intervals due to cooling time.

​Return the minimum number of intervals required to complete all tasks.
```
Example 1:

Input: tasks = ["A","A","A","B","B","B"], n = 2

Output: 8

Explanation: A possible sequence is: A -> B -> idle -> A -> B -> idle -> A -> B.

After completing task A, you must wait two cycles before doing A again. The same applies to task B. In the 3rd interval, neither A nor B can be done, so you idle. By the 4th cycle, you can do A again as 2 intervals have passed.

Example 2:

Input: tasks = ["A","C","A","B","D","B"], n = 1

Output: 6

Explanation: A possible sequence is: A -> B -> C -> D -> A -> B.

With a cooling interval of 1, you can repeat a task after just one other task.

Example 3:

Input: tasks = ["A","A","A", "B","B","B"], n = 3

Output: 10

Explanation: A possible sequence is: A -> B -> idle -> idle -> A -> B -> idle -> idle -> A -> B.

There are only two types of tasks, A and B, which need to be separated by 3 intervals. This leads to idling twice between repetitions of these tasks.
 
```

## Solution 
### My Solution

```java
class Solution {
    public int leastInterval(char[] tasks, int n) {
        if(n==0) return tasks.length;
        PriorityQueue<Integer> pq = new PriorityQueue<>((a,b)-> b-a);
        Queue<Pair<Integer,Integer>> q = new LinkedList<>();
        int time = 0;
        int[] arr = new int[26];
        for(char c:tasks) arr[c-'A']++;
        for(int val:arr){
            if(val>0) pq.add(val);
        }

        while((!pq.isEmpty())||(!q.isEmpty())){
            time++;
            if(!pq.isEmpty()){
                int val = pq.poll();
                val--;
                if(val>0)q.add(new Pair(val,time+n));
            }

            if(!q.isEmpty() && q.peek().getValue()==time){
                pq.add(q.poll().getKey());
            }
        }
        return time;
    }
}
```
