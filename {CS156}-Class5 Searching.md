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
- [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Tree and graph stratiegy
>	1. Understand the pseudocode
>	2. Know the difference between tree and graph search
>2. How to measure the performance
>	1. [[#Criteria for Strategy Evaluation]]
>	2. What b, d, m means ?

---
# In-Class Problems
## Tree search & Graph search strategy
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=96&rect=149,413,554,697&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.77]]
- **Node**: represent the states in state space
- **Expanding**: taking actions and change current state into next state
- **Frontier**：a set of all leaf nodes available for expansion at any given point
### Tree search structure
> In tree search, it doesn't check repeat nodes when expanding.
### Graph search structure
>The graph search check repeat nodes by using a "explored" set. If there are repeated node in the explored set and frontier after expanding, they will be ignored. 
## Criteria for Strategy Evaluation:
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=99&rect=123,366,525,427&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.80]]
>[!tip] Optimal solution
> [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=87&selection=118,24,122,44&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.68]]
> A optimal solution has the lowest path cost among all solutions
### How to represent complexity in AI
[[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=99&selection=107,0,129,16&color=note|Artificial Intelligence - A Modern Approach (3rd Edition), p.80]]

> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=99&selection=130,67,136,4&color=important|Artificial Intelligence - A Modern Approach (3rd Edition), p.80]])
> In AI, the graph is often represented **implicitly** by the initial state, actions, and transition model and is frequently **infinite**

- **b**: the branching factor or maximum number of successors of any node
- **d**: the depth of the shallowest goal node
- **m**: the maximum length of any path in the state space
> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=99&selection=159,27,160,86&color=important|Artificial Intelligence - A Modern Approach (3rd Edition), p.80]])
> Time is often measured in terms of the number of nodes generated during the search, and space in terms of the maximum number of nodes stored in memory.


---

# Flash Cards
