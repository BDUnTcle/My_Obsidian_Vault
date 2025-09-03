---
create date: 2024-03-25
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
  - CS/Algorithm/ShortestPath
modification date: 2024-03-25T07:54:00
type: LearningNote
sr-due: 2024-03-28
sr-interval: 2
sr-ease: 238
---

# Background & Materials
- [[Introduction to Single Source Shortest Paths]]
- [[Graphs-BFS(Breadth-First Search)]]
- Priority Queue
[Video: Dijkstra's Single Source Shortest Paths Algorithm with Example](https://www.youtube.com/watch?v=HBIoHSAsbQY&list=PLSVu1-lON6LyvJV6EwIJrcZi4ONJmQCQ5&index=3)

---
# Flash Cards & Review List
1. What kind of graphs could use Dijkstra's Algorithm to get the shortest path? (1 restriction)
2. Why it works when edges weight is non-negative and why its correct (how to prove)
3. What 'finished' and 'unfinished' really means during the process and when a vertex could be marked as 'finished'?
4. The relationship between dijkstra and BFS
5. In Dijkstra's you only relax each edge **once**
6. How to avoid negative weight edges in Dijkstra‘s
7. How fast of this algorithm？
>[!tldr]
>1. Source vertex s
>2. Using priority queue (similar with prim's MST algorithm)
>>From start vertex s, update the shortest path from s in each round, using priority queue 

---

>[!note] Dijstras's Algorithm can Find shortest paths from a start vertex to all other vertices
>>1. Directed and Undirected Graphs
>>2. **Non-negative** Edge weights
# Basic Idea
- Grow set of 'finalized' vertices known to be the closest to the start vertex.
- Relax edges out of a vertex once it is added to finalized set.
# Generic Algorithm on G = (V, E)
```
SSSPInitialize(G,s)
	for all v
		v.d=infty
		v.p=nil
	s.d=0
Relax(u->v)
	if(u.d+weight(u->v) < v.d)
		v.d = u.d + weight(u->v)
		v.p = u

Dijkstra(G,s)
	SSSPInitialize(G,s)
	for u in V
		mark u unfinished
	mark s finished
	for edge e(s->v) outgoing from s
		Relax(e)
	while unfinished vertices exist
		let u be min distance unfinished vertex
		mark u finished
		for edge e(u->v) outgoing from u
			Relax(e)
```
A vertex u is 'finished' means: you find a shortest path from start vertex s to u
Since the algorithm grow a finish-set from start vertex s, for any vertex u, once you find the shortest path from m to u, you find the shortest path from s to u (the u is a 1 out-degree vertex of m) because the shortest path from s to m must has been calculated before), and since all edge weight is non-negative, its correct.
# Analysis
## Without using any extra data structures
Runtime: $Θ(V^2+E)=Θ(V^2)$, including:
- Initialization: $Θ(|V|)$
- |V| finding minimum operations
- |E| relaxations
## Using Binary Heap Priority Queue
- Initialization: $Θ(|V|)$
- Find minimum: $O(lg|V|)$
- Relaxation and changeKey: $O(lg|V|)$
- Total：$O((|V|+|E|)lg|V|)=O(|E|lg|V|)$
## Using Fibonacci Heap Priority Queue
- Initialization: $Θ(|V|)$
- |V| Find minimum: $O(|V|lg|V|)$
- |E| Relaxation: $O(|E|)$
- Total：$O(|E|+|V|lg|V|)$
# Optimizations
## 1. Using priority queue to handle "sparse graph"
>[!tip] Using Fibonacci heap priority queue is asymptotic better than using binary heap priority queue
```
SSSPInitialize(G,s)
	for all v
		v.d=infty
		v.p=nil
	s.d=0
Relax(u->v)
	if(u.d+weight(u->v) < v.d)
		DecreaseKey of v in Q
		v.d = u.d + weight(u->v)
		v.p = u
		
Dijkstra(G,s)
	SSSPInitialize(G,s)
	Q = new MinPriorityQueue(V)
	While Q not Empty
		 u = Q.DeleteMin()
		 for edge e(u->v) outgoing from u
			 Relax(e)
```
# The relationship between Dijkstra's with BFS
>When change the priority queue to a FIFO queue and make all edge weight to be 1, it is BFS

# Using Dijkstra's with negative edge weight
>[!question] Is that must be wrong when Using Dijkstra's with negative edge weight?
>> The answer is not always wrong. Maybe it works well
 
<mark style="background: #FFB8EBA6;">The important point is not that there are negative weight edges, but when there are negative weight edges, the algorithm process could try to modify a vertex's distance which has been done before, and when a vertex's shortest distance is changed, there is a need to relax all out edges of it. However, the dijkstra's don't relax edge more than one time.</mark>
So, we could add a simple judgement in relax to check if there is a negative weight edge during the process
```
Relax(u->v)
	if(u.d+weight(u->v) < v.d)
		if v not in Q, faill   //check if there is a negative weight edge
		DecreaseKey of v in Q
		v.d = u.d + weight(u->v)
		v.p = u
```
---
# Examples
[[Dijstra SSSP.excalidraw]] 

|           | A   | B   | C   | D   | E   | F   | G   | S (Start) |
| --------- | --- | --- | --- | --- | --- | --- | --- | --------- |
| A         |     | 3   |     |     |     |     |     |           |
| B         | 1   |     | 4   |     | 0   |     |     |           |
| C         |     | 0   |     |     |     |     |     |           |
| D         |     |     |     |     | 13  | 3   |     |           |
| E         |     |     | 0   |     |     | 3   |     |           |
| F         |     |     | 8   | 4   |     |     |     |           |
| G         |     |     |     |     |     | 5   |     |           |
| S (Start) | 8   |     |     | 2   |     | 7   | 3   |           |
1. Initialization: the priority queue Q={S, A, B, C, D, E, F, G}

DIJKSTRA algorithm with each vertex‘s shortest path from start and its descendant after every round

|     | 1st round | 2nd round (D) | 3rd round (G) | 4th round (F) | 5th round (A) | 6th round (B) | 7th round (E) | 8th round (C) |
| --- | --------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| A   | 8, S      |               |               |               |               |               |               |               |
| B   | -         |               |               |               | 11, A         |               |               |               |
| C   | -         |               |               | 13, F         |               |               | 11, E         |               |
| D   | 2, S      |               |               | -             |               |               |               |               |
| E   |           | 15, D         |               |               |               | 11, B         |               |               |
| F   | 7, S      | 5, D          | -             |               |               |               |               |               |
| G   | 3, S      |               |               |               |               |               |               |               |
| S   | -         | -             |               |               |               |               |               |               |

---
