### Algorithm

1. Given an array, each element in the array has to be greater than 1 and less than n - size of the array 
Find all duplicates in the array in O(n) and without O(n) space complexity 

Implementation Detail: Inplace 

Gameplan: 
The hint lies in the restraints, each value in the array has to be greater than 1 and less than n. In other words in a perfect 
world, all of the values can map to all of the indices 
For example: 

indices - 0 1 2 3 4 5 6 7 
          1 2 3 4 5 6 7 8 

Here we don't have any duplicates however, every index has it's individual value, and every value has it's own index 
Le'ts say we add duplicates 

indices - 0 1 2 3 4 5 6 7 
          4 2 1 2 3 4 5 6 
Here the duplicates share the same index, knowing that if we used the values as keys and marked the negatives
Whenever we hit another negative we know this value has already been hit and therefor is a duplicate 

Also we have to account for the -1 since the indices are from 0 to n-1, and the values are from 1 to n 

res - holds all of the duplicates 

loop through the given array 
  make the current value into an index and check if it's positive
    if it is, turn to negative 
  if not, means that a duplicate is found
    append to res 


### Solution
class Solution:
    def findDuplicates(self, nums: List[int]) -> List[int]:
        
        res = [] 
        
        for x in nums: 
            if nums[abs(x)-1] > 0: 
                nums[abs(x)-1] *= -1
            else: 
                res.append(abs(x))
                
        
        return res
```

### Time/Space Complexity

-  Time Complexity: O(N)
- Space Complexity: No extra space
