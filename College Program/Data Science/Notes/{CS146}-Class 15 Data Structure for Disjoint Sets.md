---
create date: 2024-03-17
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
-  [[《2009 Introduction to Algorithms Third Ed》.pdf]] Ch 21-21.3 (p.582)
-  [Video: Disjoint Sets: the Union-Find Data Structure. The comments contain a link to an updated version.](https://www.youtube.com/watch?v=j8uAsZbBD7U)

[[Drawing 2024-03-17 13.32.56.excalidraw]]

---
# Review List
>[! abstract] Main Topics
>1. Basic Concepts and Definition
>2. Basic operations: make, union, find
>3. Link-list representation and implements
>4. Tree representation and implements
>5. 2 heuristics to improve the runtime
>	1. Union by rank and how it improve the runtime
>	2. Path compression and how it improve the runtime

---
# In-Class Problems
## Definition and Basic Operations
A disjoint-set data structure maintains a collection $S={S_1, S_2, S_3,..., S_k}$ of disjoint dynamic sets
Each set in it is identified as *representative*
>Operations: x is an object
- **Make-Set (x)**: Create a new set whose only member is x, x not  in other set
- **Union (x, y)**: Unite the dynamic sets that contain x and y, say $S_x$ and $S_y$ into a new set
- **Find-Set (x)**: Return a pointer to the representative of the set contain x
## Linked-list representation of disjoint sets
- *head*：pointing to the first object(*representative*) in the list
- *tail*：pointing to the last object
### Analysis and optimization
## Rooted tree representation of disjoint sets & disjoint-set forests
- each node containing one member
- each tree representing one set
- the root node is representative and is its own parent
### 2 heuristics to improve the running time
#### Union by rank/size
#### path compression

>[!note] Runtime
>>1. Use union by rank or size alone: $O(mlg^n)$
>>2. Use path compression alone: $O(n+f*(1+log_{2+f/n}^n))$, n make-set and f find-set
>>3. Use both 1 and 2: $O(m*\alpha(n))$, in which $\alpha(n)$ is a very slowly growing function
---
# Flash Cards
