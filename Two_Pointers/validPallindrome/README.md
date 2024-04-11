
# Valid Palindrome

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.
```
Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

## Solution 
### Removing all non Alphanumeric characters

```java
public static String removeNonAlphabeticAndLowercase(String input){
        StringBuilder result = new StringBuilder();
        for(int i=0;i<input.length();i++){
            Character ch = input.charAt(i);
            if(Character.isLetterOrDigit(ch)){
                result.append(Character.toLowerCase(ch));
            }
        }
        return result.toString();
    }
```

#### Space complexity : O(1)
#### Time complexity: O(n)

### Now finding pallindrome using 2 pointers approach

```java
public static boolean isPalindromeOrNot(String input){
    int i = 0;
    int j = input.length()-1;
    while(i<j){
        if(input.charAt(i)!=input.charAt(j)){
            return false;
        }
        i++;
        j--;
    }   
    return true; 
    }
```
#### Space complexity : O(1)
#### Time complexity: O(n)
## combined 

```java
public boolean isPalindrome(String s) {
        
    int i = 0;
    int j = s.length() - 1;
    while (i < j) {
        
        Character start = s.charAt(i);
        Character end = s.charAt(j);
        
        if (!Character.isLetterOrDigit(start)) {
            i++;
            continue;
        }
        
        if (!Character.isLetterOrDigit(end)) {
            j--;
            continue;
        }
        
        if (Character.toLowerCase(start) != Character.toLowerCase(end)) {
            return false;
        }
        
        i++;
        j--;    
    }
    
    return true;
}
```

