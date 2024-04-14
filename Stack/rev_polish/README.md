
# Evaluate Reverse Polish Notation

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.
 
```
Example 1:

Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
Example 2:

Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
Example 3:

Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
 
 
```

## Solution 
### my solution
```java
public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();
        int res;
        for(String token:tokens){
            if(token.equals("+")){
                stack.push(stack.pop()+stack.pop());
            }
            else if(token.equals("-")){
                stack.push(-stack.pop()+stack.pop());
            }
            else if(token.equals("*")){
                stack.push(stack.pop()*stack.pop());
            }
            else if(token.equals("/")){
                int a,b;
                a=stack.pop();
                b=stack.pop();
                stack.push(b/a);
            }
            else{
                stack.push(Integer.parseInt(token));
            }
        }
        return stack.pop();
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n)

### better solution

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> st = new Stack<>();
        int x,y;
        for(int i = 0;i< tokens.length;i++) {
            String str = tokens[i];
            switch(str){
                case "+":
                    y = st.pop();
                    x = st.pop();
                    st.push(x+y);
                    break;
                case "-":
                    y = st.pop();
                    x = st.pop();
                    st.push(x-y);
                    break;
                case "*":
                    y = st.pop();
                    x = st.pop();
                    st.push(x*y);
                    break;
                case "/":
                    y = st.pop();
                    x = st.pop();
                    st.push(x/y);
                    break;
                default:
                    st.push(Integer.parseInt(str));
            }
        }
        return st.pop();
    }
}
```

#### Space complexity : O(1)
#### Time complexity: O(n)
