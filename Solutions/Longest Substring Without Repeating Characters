### Algorithm

1. Given a string find the longest substring without repeating characters

Implementation Detail: Hashmap - lookup time is O(1)

### Solution
  maxLength - keeps track of the maxLength, this is what will be returned 
  start - A index value that represents the beginning of the substring 
  usedChar - Key value pair dictionary that maps chars to the index they appeared
  
  gameplan 
    Loop through input string 
      if current char appeared before and it exists after the start of the current substring 
        update start to start on one index after old char 
      else - current char does not repeat, update maxLength 
        compare maxLength to itself and the length of the substring (i - start + 1) 
      update the current char's position 
    
    return maxLength

```Python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        
        maxLength = start = 0 
        usedChar = {}
        
        for i in range(len(s)):
            if s[i] in usedChar and start <= usedChar[s[i]]:
                start = usedChar[s[i]] + 1
            
            else: 
                maxLength = max(maxLength, i - start + 1)
            
            usedChar[s[i]] = i
        
        return maxLength
```

### Time/Space Complexity

-  Time Complexity: O(n)
- Space Complexity: O(n)
