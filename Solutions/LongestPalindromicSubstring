Algorithm

    Given a string s, find the longest palindromic substring (not subsequence) in s 

Implementation Detail:

Gameplan: 
We have to use two pointers because we might need to keep track of a character that was already in a previous 
found palindrome 

Start - Keeps track of the start of the possible palindrome 
End - Keeps track of the end of the palindrome 
res - A list of all of the found palindromes 

Keep incrementing end until end > len(s)
  When this happens increment start, but skip to the length of the currently longest palindrome to save time, form of DP 
 
Otherwise keep incrementing end 


    

Solution

def longestPalindrome(self, s: str) -> str:
        start = 0 
        end = 1 
        res = [] 
        
        if not s: 
            return ""
        
        while start < len(s): 

            if end > len(s): 
                start += 1
                end = start + (len(res[-1]) if len(res) != 0 else 1)

            elif s[start:end] == s[start:end][::-1]: 
                res.append(s[start:end])
                end += 1
       
            else: 
                end += 1
        
        return res[-1]

Time/Space Complexity

    Time Complexity: O(n)
    Space Complexity: ?
