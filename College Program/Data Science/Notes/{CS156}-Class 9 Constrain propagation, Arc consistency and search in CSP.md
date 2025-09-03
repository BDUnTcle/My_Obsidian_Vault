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
>1. What is [[#Inference and constraint propagation in CSP]]
>2. Standard search formulation (incremental)
>3. [[#Backtracking search for CSPs]]
>	1. Understand pesudocode for it
>	2. Know [[#Optimizations of backtracking search]]
>4. [[#Arc Consistency]]
>	1. Know what arc consistency and network arc consistency are

---
# In-Class Problems
## Inference and constraint propagation in CSP
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=227&rect=52,564,528,662&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.208]]
- ~ constraint propagation can be a optimization approach in backtracking search
## Backtracking search for CSPs
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=234&rect=149,383,552,699&color=note|Artificial Intelligence - A Modern Approach (3rd Edition), p.215]]
## Arc Consistency
A variable in a CSP is arc-consistent if every value in its domain satisfies the variable’s **binary constraints**
 
>[!note] $X_{i}$ is arc-consistent with respect to another variable $X_{j}$ if for every value in the current domain Di there is some value in the domain Dj that satisfies the binary constraint on the arc $(X_{i} ,X_{j})$
>>[!example]
>>For constrain: $Y=2X$
>> $X \in \{2,3,4,5\}$
>> $Y \in \{4,6,8,10,12,22\}$
>> Then  X arc-consistent with respect to Y, but Y doesn't arc-consistent with respect to X. because 12 and 22 in Y can not find a pair in X which match the constrain.
>> Only when $Y \in \{4,6,8,10\}$，both X and Y arc-consistent with respect to each other

A network is arc-consistent if every variable is arc consistent with every other variable
### AC-3 algorithms
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=228&rect=147,393,552,698&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.209]]
### Optimizations of backtracking search
>[!example] 4 intuitive idea
>1. Which variable should be assigned next  and in what order should its values be tried?
>2. What inferences should be performed at each step in the search?
>3. Can we detect inevitable failure early?
>4. Can we take advantage of problem structure?
#### For variable and value ordering
>[!example] for variable selection
- @ The **MRV** (Minimum remaining values): *powerful*
	- Choosing the variable with the fewest "legal" values
- @ The **degree heuristic** *tie-breaker*
	- Select the variable that is involved in the largest number of constrains on other unassigned variables
>[!example] for value selection
- @ The **least-constraining-value**
	- Choose the value that rules out the fewest choices for the neighboring variables in the constrain graph
#### Interleaving search and inference
- @ **Forward checking**: (does not detect all inconsistencies)
	- Whenever a variable X is assigned, establish arc consistency for it; for each unassigned variable Y that is connected to X by a constraint, delete from Y's domain any value that is inconsistent with the value chosen for X
- @ **MAC**(Maintaining Arc Consistency)
	- After variable $X_{i}$ is assigned, call [[#AC-3 algorithms]] but start with only the arcs $(X_{j},X_{i})$ for all $X_{j}$ that are unassigned variables that are neighbors of $X_{i}$ instead of a queue of all arcs in CSP
---

# Flash Cards
