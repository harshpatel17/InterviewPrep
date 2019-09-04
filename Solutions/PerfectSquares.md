### Algorithm

1. Given an integer n, find the least number of perfect squares that sum to n, doubles are allowed 

Implementation Detail: BFS, shortest distance  

Gameplan: 
Check all possible numbers, once you find the right path keep going
x==y means that x-y will be zero 

squares - contain all of the perfect squares upto the value n 
toCheck - Numbers we need to check that might be a solution or a part of the solution 
cnt - Keeps track of how many perfect squares, return this value 
temp - empty set 

Create squares 
toCheck is a set that starts off with n 
while toCheck is not empty 
  temp = empty set 
  loop through toCheck (x) 
    loop through squares (y) 
      if x == y then return cnt 
      if y > x then break out of this loop 
      add(x-y) to temp 
    toCheck = temp 
      
return x


### Solution

```Python
class Solution:
    def numSquares(self, n: int) -> int:
        
        if n == 1: 
            return n 
        
        squares = [] 
        i = 1
        while i*i <= n: 
            squares.append(i*i)
            i += 1
        
        toCheck = {n}
        cnt = 0 
        
        while toCheck: 
            cnt += 1
            temp = set() 
            for x in toCheck:
                for y in squares: 
                    if x == y: 
                        return cnt
                    if x < y: 
                        break 
                    temp.add(x-y)
            toCheck = temp 
        
        return cnt
```

### Time/Space Complexity

-  Time Complexity: ??
- Space Complexity: ??
