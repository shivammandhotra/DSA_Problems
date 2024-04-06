
# Group Anagrams

## Problem Link
https://leetcode.com/problems/group-anagrams/description/

## Description
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Examples 
```
Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
Example 2:

Input: strs = [""]
Output: [[""]]
Example 3:

Input: strs = ["a"]
Output: [["a"]]
```

## Solution

### Approach
```
HashMap<String, String> hashMap = new HashMap<>(); 

for(i=0->n){
String str = strs[i];
str.sort();
if(hashMap.containsKey(str)){
	hashMap.add() -> we have to make a chain of all the strings for that category without overriding the key, how? By having a list of String attached to the hash value
}
}

```

#### rather than defining this
HashMap<String, String> hashMap = new HashMap<>(); 
#### we will be defining this
HashMap<String,List<String>> hashMap = new HashMap<>

#### Sorting of the String: str.sort(); -> 

```
char[] str = strs[i].toCharArray();
Arrays.sort(str);
String newStr = new String(str);

```



### Solution

```java
public List<List<String>> groupAnagramDSSort(String[] strs) {
        HashMap<String,List<String>> hashMap = new HashMap<>();
        int n = strs.length;
        for(String str:strs){
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String newStr = new String(chars);

            if(hashMap.containsKey(newStr)){
                hashMap.get(newStr).add(str);
            }
            else{
                hashMap.put(newStr, new ArrayList());
                hashMap.get(newStr).add(str);
            }
        }
        return new ArrayList<>(hashMap.values());
    }
```
#### Time Complexity: O(nlogn)
#### Space Complexity: O(n)