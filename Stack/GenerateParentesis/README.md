
# Generate Parentheses

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
 
```
Example 1:

Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]

Example 2:

Input: n = 1
Output: ["()"]
```

## Solution 

### My Solution
```java
class Solution {
    private Stack<Character> stack = new Stack<>();
    private List<String> result = new ArrayList<>();
    public List<String> generateParenthesis(int n) {
        backtrack(0,0,n);
        return result;
    }

    public void backtrack(int openN,int closedN, int n){
        if(openN==closedN && closedN==n){
            Iterator val = stack.iterator();
            String temp = "";
            while(val.hasNext()){
                temp = temp+val.next();
            }
            result.add(temp);
        }
        if(openN<n){
            stack.push('(');
            backtrack(openN+1,closedN,n);
            stack.pop();
        }
        if(closedN<openN){
            stack.push(')');
            backtrack(openN,closedN+1,n);
            stack.pop();
        }
    }
}
```

#### Space complexity : O(n)
#### Time complexity: O(nlogn)?

### nice solution

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        helper(result, 0, 0, "", n);
        return result;
    }
    private void helper(List<String> result, int left, int right, String s, int n) {
        if (s.length() == 2 * n) {
            result.add(s);
            return;
        }
        if (left < n) {
            helper(result, left + 1, right, s + "(", n);
        }
        if (right < left) {
            helper(result, left, right + 1, s + ")", n);
        }
    }
}
```

