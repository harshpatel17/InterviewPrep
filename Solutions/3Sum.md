### Algorithm

1. Find all unique triplets such that a+b+c = 0

Implementation Detail: 

Gameplan: 
Loop through the nums array and represent i as a target
After the target index we will have 2 pointers
  l - starts 1 index after the target and moves from left to right 
  r - starts at the last index and moves from right to left 
Account for repeated targets by skipping the next value 

total = nums[l] + nums[r] + nums[i] (target) 
if total is < 0, move l to the right 
if total is > 0, move r to the left 
Account for repeated values 


### Solution

```Python
def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()
        for i in range(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if s < 0:
                    l +=1 
                elif s > 0:
                    r -= 1
                else:
                    res.append((nums[i], nums[l], nums[r]))
                    while l < r and nums[l] == nums[l+1]:
                        l += 1
                    while l < r and nums[r] == nums[r-1]:
                        r -= 1
                    l += 1; r -= 1
        return res
```

### Time/Space Complexity

-  Time Complexity: O(n)
- Space Complexity: O(n)
