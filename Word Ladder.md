### Algorithm

Given a beginWord and endWord, and a wordList. What is the shortest path from beginWord to endWord through using the wordlist. You can
change one letter at a time. 

Implementation Detail: dict, deque, preprocessing 

Gameplan: 
Shortest path makes me think can this problem be a graph problem? 
Yes it is, the vertices of the graph can be a common connection
ex. hot --> *ot --> dot 
*ot is the common vertices 
Once we get to the endWord, we have found the shortest path 

Preprocess the wordlist
*ot ['hot', 'dot', 'lot']
h*t ['hot']
ho* ['hot']
d*t ['dot']
do* ['dot', 'dog']
*og ['dog', 'log', 'cog']
d*g ['dog']
l*t ['lot']
lo* ['lot', 'log']
l*g ['log']
c*g ['cog']
co* ['cog']

defaultdict with a list as values 

Have a visted dictionary 

Create a deque 
  Pop the deque 
  find the preprocessed values for the deque 
  Check in the preprocessed wordlist for what words are common and add to dequeue
  If common word equals endWord, return level + 1 



### Solution

```Python
from collections import defaultdict
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        
        L = len(beginWord)
        
        if endWord not in wordList or not beginWord or not endWord or not wordList:
            return 0
        
        #Preprocess
        processed_words = defaultdict(list)
        
        for word in wordList: 
            for i in range(L):
                processed_words[word[:i] + '*' + word[i+1:]].append(word)
        
        visited = {beginWord:True}
        
        q = collections.deque([(beginWord,1)])
        
        while q: 
            current_word,level = q.popleft()
            
            for i in range(L): 
                inter_word = current_word[:i] + '*' + current_word[i+1:]
                for word in processed_words[inter_word]:
                    if word == endWord: 
                        return level + 1 
                    
                    if word not in visited: 
                        visited[word] = True 
                        q.append((word,level+1))
            processed_words[inter_word] = [] 
        return 0
```

### Time/Space Complexity
Time complexity - O(M*N)
Space complexity - O(M*N)
