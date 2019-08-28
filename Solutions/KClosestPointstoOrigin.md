### Algorithm

We have a list of points on a plane, find the K closest points to the origin (0,0) 
K will be given 

Implementation Detail: Minheap

Gameplan: 
import heapq (part of the standard python library) 
loop through the points 
  find the euclidean distance (we want to make this negative so it acts as a maxheap instead of a minheap) 
  We want need to return the distance so it's fine if it's negative 
  
  the max length of the heap can only be K 
    if it exceeps that we want to implement heapq.heappushpop
  else or if the length of the heap is less than K 
    We just want to push - heapq.heappush


### Solution

```Python
import heapq
class Solution:
    def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
        heap = [] 
        
        for (x,y) in points: 
            dist = -(x*x + y*y)
            
            if len(heap) == K: 
                heapq.heappushpop(heap,(dist,x,y))
            
            else: 
                heapq.heappush(heap,(dist,x,y))
        
        return [(x,y) for (dist,x,y) in heap] 
```

### Time/Space Complexity

Inserting an item into the heap takes O(logk) times, k is the length of the heap 
We loop throught points n times so: 
Time complexity - O(n*logK)
Space complexity - O(K)
