
# Longest Substring Without Repeating Characters 

Given a string s, find the length of the longest 
substring
 without repeating characters.
 
```
Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

## Solution 

### My Solution
```java
public int lengthOfLongestSubstring(String s) {
        HashMap<Character,Integer> hash = new HashMap<>();
        int n = s.length(),left=0,right=0,len,maxlen=0;
        while(right<n){
            char ch = s.charAt(right);
            if(hash.containsKey(ch)){
                if(hash.get(ch)>=left){
                    left = hash.get(ch)+1;
                }
            }
            len = right - left + 1;
            maxlen = Math.max(maxlen, len);
            hash.put(ch,right);
            right++;
        }
        return maxlen;
    }
```

### solution link https://www.youtube.com/watch?v=-zSxTJkcdAo&t=1108s

