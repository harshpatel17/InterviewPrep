### Algorithm

1. Find all duplicate subtrees in the given binary tree, return as a list of treenodes

Implementation Detail: TreeNode to tuple 

Gameplan: 
One good way of finding duplicates it using a dictionary, when a key has multiple values you have found your duplicates 

Convert TreeNode to tuples - makes hashing easier 
Make the tuples keys, while the root is the value 

return all of the values that have more than one value in a key 


### Solution

```Python
class Solution:
    def findDuplicateSubtrees(self, root: TreeNode) -> List[TreeNode]:
        
        def tuplify(root):
            if root: 
                tuple = root.val, tuplify(root.left), tuplify(root.right)
                trees[tuple].append(root)
                return tuple 
        
        trees = collections.defaultdict(list)
        tuplify(root)
        return [roots[0] for roots in trees.values() if len(roots) > 1]
```

### Time/Space Complexity

-  Time Complexity: O(n^2)
- Space Complexity: O(n)
