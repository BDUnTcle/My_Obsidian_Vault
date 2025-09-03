---
create date: 2024-03-12
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - CS/Algorithm
  - CS
modification date: 
type: CourseNotes
sr-due: 2024-03-16
sr-interval: 1
sr-ease: 190
---
# Before the Class
## Lectures and Materials
- [[《2009 Introduction to Algorithms Third Ed》.pdf]]
	- Ch 22.4-22.5
- [[Topological Sorting]]

---
# Review List
>[! abstract] Main Topics
>- Topological ordering concept and representation
>- 2 algorithms for Topological Sorting
>
>>[!note] Khan's algorthm
>>1. Find in-degree list
>>2. Start from 0 in degree vertex, keep decreasing in-degree list until there is no 0 in degree vertices
>>Runtime: $Θ(E)$
>
>>[!note] DFS
>>1. Run DFS
>>2. The topological order is sorted by the finish time of vertex (the last finished vertex is in the first in topological order)
>>Runtime: $Θ(V+E)$
>
>- Concepts and algorithm of **Strongly Connected Components**
>- [[#Semi-Connected Graph]]
---
# In-Class Problems
## Topological Sorting 
### Concept
>[!note] Two different Sorting Concepts
>>1. Fully Ordered Sets
>>	- like sort a sequence of numbers: 12<50<88 
>>2. Partially Ordered Sets (**Topological order**)
>>	- Calculus I < Calculus II but dosen't matter when you take the Shakespeare Course
### Representation : 
a DAG with every vertex represent a unit needed to be sort.
### Algorithms:
#### Kahn's Algorithm

 >[!tip] General Thoughts
 >1. A vertex with no **incoming** edges can go **first**
 >	1. DAG must contain a vertex with no incoming edges
 >2. No need to start from scratch each time (Optimitation)
 >	1. Compute incoming adjacency list just once to start
 >	2. Grab a set of all 0 in-degree vertices
 >	3. Find new 0 in-degree vertices as vertices are removed from the graph
 >3. Clean up:
 >	1. Remove vertices from incoming adjacency lists, not from the graph as a whole
 >	2. No need to keep 2 different ordered sets, with the same order
 >4. We don't care what incoming edges are, only the in-degree
```
TopSort(G)
	create incoming edge adjacency list for each vertex -(optimization)-> **find in-Degree** for each vertex
	S = ordered list
	add all vertices with no incoming edges to S
	while not done with S
		consider next vertex u from S
		/******************could be optimized**********************
		put u next in the topological ordering
		while removing u and its outgoing edges from G
			if vertex v's incoming edge becomes empty
				add v to S
		**********************************************************/
		//optimization
		for each outgoing edge u->v
			decrement v's indegree
			if v's indegree is 0
				add v to S
```
##### Runtime
Lineral time

---
#### DFS for Topological Sort 
 >[!tip] General Thoughts
 >1. A vertex with no **outcoming** edges can go **last**
 >2. A vertex must go before everything they can reach
 >3. Once everything reachable by a vertex has reserved later times, a vertex can go after the unscheduled remaining vertices
 
 >[!question] Why DFS works so simple? 
 >> 1. There is no back edge in a DAG
 >> 2. Other 3 kinds of edges all represent the Topological order

---
## Kosaraju's Algorithm for Strongly Connected Components
>[!Abstract] Basic Concepts
>1. Components
>	1. In undirected graph
>	2. In directed graph
>2. Two vertices are **Strongly Connected** if each has a path to the other
>3. Graph G is **Strongly Connected** if all vertices in G are Strongly Connected
```
List n = DFS(G);
G2 = reverse(G);
DFS(G2) as the order of n
```
---
## Semi-Connected Graph
Give an algorithm to determine if a graph is semi-connected
1. For each u and v DFS on u and v, check that at least one can reach the other $(O (|V|^2|E|))$
2. For each v, DFS to see what it can reach, for each u, v determine if u~>v or v~>u($O (VE)$)
3. Find strongly connected components in the graph, determine whether they are semi-connected
	1. This makes the new graph become acyclic, which you can topological sorting the graph
	2. After topological sorting, if every vertex can reach all vertices right of it, the graph is semi-connected


---

# Flash Cards
