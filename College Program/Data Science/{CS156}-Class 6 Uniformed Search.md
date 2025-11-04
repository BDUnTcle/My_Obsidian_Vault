---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
---
# Review List
>[! abstract] Main Topics
>1. know about [[#BFS]]
>2. know about[[#Uniform-Cost Search]]
>	1. Understand  [[#Compare BFS with Uniform-cost Search]]
>3. Know about [[#DFS]]
>	1. Know [[#The advantage of DFS]]
>	2. Why DFS is non-optimal and non-completed?
>4. Know about [[#Depth-limited Search]]
>	1. Know the relationship between DFS and DLS
>5. Know about [[#Iterative Deepening Search]]

---
# In-Class Problems
### BFS
>[!note] also refer to [[Graphs-BFS(Breadth-First Search)]]
>>Basic idea: expand root node first, then expand all the successors of the root node, then their successors...

![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=101&rect=123,481,529,697|Artificial Intelligence - A Modern Approach (3rd Edition), p.82]]
- **Completeness**: Yes 
- **Optimality**: Yes
- **Time Complexity**: $O(b^d)$
- **Space Complexity**: $O(b^d)$
### Uniform-Cost Search
>[!tip] Idea of Uniform-Cost Search
>> Instead of expanding the shallowest node, uniform-cost search expands the node n with the **lowest path cost** $g(n)$, by storing the frontier as a *priority queue*

![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=103&rect=123,492,530,697&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.84]]
- **Completeness**: Yes (only if the step cost is nonnegative) 
- **Optimality**: Yes
- **Time Complexity**: $O(b^{1+[c*/\epsilon]})$
- **Space Complexity**: $O(b^d)$
#### Compare BFS with Uniform-cost Search
- @ the goal test in Uniform-cost search is applied to a node when it is selected for expansion rather than when it is first generated
- @ a test is added in uniform-cost search in case a better path is found to a node currently on the frontier
- @ When all step costs are qual, those 2 are simillar
- @ the complexity of uniform-cost search can be much greater than BFS, because uniform-cost search can explore large trees of small steps before exploring paths involving and perhaps useful steps
### DFS
>[!note] also refer to [[Graphs-DFS(Depth-First Search)]]
>>Using LIFO queue rather than FIFO queue in BFS
- **Completeness**: 
	- For tree-search version, it is not complete
- **Optimality**: No
- **Time Complexity**: $O(b^{m})$
- **Space Complexity**: $O(bm)$, $O(m)$ if use backtracking 
#### The advantage of DFS
> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=106&selection=32,25,38,37&color=note|Artificial Intelligence - A Modern Approach (3rd Edition), p.87]])
> The reason is the **space complexity**. For a graph search, there is no advantage, but a depth-first tree search needs to store only a single path from the root to a leaf node, along with the remaining unexpanded sibling nodes for each node on the path. Once a node has been expanded, it can be removed from memory as soon as all its descendants have been fully explored.

### Depth-limited Search
>[!tip] idea of Depth-limited Search
>> To solve the infinite state space of DFS, by adding  a depth limit $l$

![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=107&rect=123,488,529,698|Artificial Intelligence - A Modern Approach (3rd Edition), p.88]]
- **Completeness**: 
	- Similar with DFS, incompleted if $l<d$
- **Optimality**:
	- No if $l>d$
- **Time Complexity**: $O(b^{l})$
- **Space Complexity**: $O(bl)$, $O(l))$ if use backtracking 

### Iterative Deepening Search
> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=107&selection=291,0,291,86&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.88]])
> Often used in combination with depth-first tree search, that finds the best depth limit.

![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=108&rect=143,616,554,687&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.89]]
- **Completeness**: 
	- Yes, if the branching factor is finite
- **Optimality**:
	- Yes, if the path cost is a nondecreasing function of the depth of the node
- **Time Complexity**: $O(b^{d})$
- **Space Complexity**: $O(bd)$, $O(d))$ if use backtracking 
---
## Comparing Uniformed Search 
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=110&rect=142,133,554,285&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.91]]

---

# Flash Cards
