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
>1. Know the basic concepts of best-first search
>	1. What is [[#Evaluation function $f(n)$]]
>	2. What is [[#Heuristic function $g(n)$]]
>2. Know [[#Greedy search]]
>	1. Why its not optimal and incomplete
>3. Know [[#A* search]]

---
# In-Class Problems
## Best-first search concepts
> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=111&selection=78,28,88,28&color=important|Artificial Intelligence - A Modern Approach (3rd Edition), p.92]])
>  The implementation of best-first graph search is identical to that for uniform-cost search (Figure 3.14), except for the use of f instead of g to order the priority queue.

### Evaluation function $f(n)$
- % The evaluation function is construed as a **cost estimate**, so the node with the **lowest** evaluation is expanded first.
### Heuristic function $g(n)$
- % the heuristic function is the estimate cost of the cheapest path from the state at node n to a goal
## Greedy search
>[!tip] Try to expand the node that is closest to the goal
>> $f(n)=h(n)$
>
- **Completeness**: 
	- No
- **Optimality**:
	- No
- **Time Complexity**: $O(b^{m})$
- **Space Complexity**: $O(b^m)$
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=87&rect=121,433,526,704|Artificial Intelligence - A Modern Approach (3rd Edition), p.68]]
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=112&rect=145,561,554,705&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.93]]

## A* search
>[!tip] idea of A* search
>> $f(n)=g(n)+h(n)$
>> $g(n)$ is the path cost from the **start node** to node $n$
### Optimizations
#### Make $h(n)$ admissible heuristic
- % admissible heuristic: it *never over estimate*
#### Consistency/monotonicity

![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=118&rect=147,452,552,696&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.99]]

---

# Flash Cards
