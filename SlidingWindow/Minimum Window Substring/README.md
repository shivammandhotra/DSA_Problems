
#   Minimum Window Substring

### Problem Link 
##### https://leetcode.com/problems/minimum-window-substring/description/
### Description
Given two strings s and t of lengths m and n respectively, return the minimum window 
substring
 of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.
```
Example 1:

Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.

Example 2:

Input: s = "a", t = "a"
Output: "a"
Explanation: The entire string s is the minimum window.

Example 3:

Input: s = "a", t = "aa"
Output: ""
Explanation: Both 'a's from t must be included in the window.
Since the largest window of s only has one 'a', return empty string.
```

## Solution 
#### See https://www.youtube.com/watch?v=hz4duBZEZ3I  for reference
```java
public String minWindow(String s, String t) {
        HashMap<Character,Integer> map = new HashMap<>();
        for(char ch: t.toCharArray()){
            map.put(ch,map.getOrDefault(ch,0)+1);
        }

        int matched = 0;
        int start = 0;
        int minLen = s.length() +1;
        int subStr = 0;

        for(int i=0;i<s.length();i++){
            char right = s.charAt(i);
            if(map.containsKey(right)){
                map.put(right,map.get(right)-1);
                if(map.get(right)==0) matched++;
            }
            while(matched==map.size()){
                if(minLen>i-start+1){
                    minLen = i-start+1;
                    subStr = start;
                }
                char deleted = s.charAt(start);
                start++;
                if(map.containsKey(deleted)){
                    if(map.get(deleted)==0) matched--;
                    map.put(deleted,map.get(deleted)+1);
                }

            }
        }
        return minLen>s.length()?"":s.substring(subStr,subStr+minLen);
    }
```



