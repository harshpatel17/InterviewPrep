### Algorithm

1. Flatten binary tree to linked list but do it in place 

Implementation Detail: Inplace, BT

Gameplan: 
Think of ways you would solve this intuitvely 
Create a global variable called prev
  This will keep track of the prev values
Traverse right, then left, then evaluate the root 
root.right = self.prev - attach previous to the right root
root.left = None - make left none
self.prev = root - update prev root


### Solution
class Solution:
    prev = None
    def flatten(self, root: TreeNode) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        if not root: 
            return None 
        
        self.flatten(root.right)
        self.flatten(root.left)
        
        root.right = self.prev
        root.left = None 
        self.prev = root 
        
        return root
```

### Time/Space Complexity

-  Time Complexity: O(N) - Since we are visiting all of the nodes
- Space Complexity: No extra space
