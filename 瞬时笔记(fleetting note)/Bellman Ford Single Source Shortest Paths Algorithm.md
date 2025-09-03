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
- [[Introduction to Graph]]
- [[Graphs-BFS(Breadth-First Search)]]

[Video: Bellman Ford Single Source Shortest Paths Algorithm with Example](https://www.youtube.com/watch?v=7KGohCDej1s&list=PLSVu1-lON6LyvJV6EwIJrcZi4ONJmQCQ5&index=2)

# Flash Cards & Review List
1. [[#What is Negative Weight Cycles]]？
	1. Why it bothers us in finding SSSP?
	2. How to mark it? (2 keys)
2. What kind of graphs could use Bellman Ford Algorithm to get the shortest path? (3 keys)
3. Why it works and why its correct (how to prove)
>[!tldr]
> Has start vertex s
> Each round, relax every edge and update the shortest path from s

---
>[!note] Bellman Ford Algorithm can Find shortest paths from a start vertex to all other vertices
>>1. Works in any graph
>>2. Work for any edge weights
>>3. Detects reachable negative weight cycles
# Basic Idea
>[!question] What is **Negative Weight Cycles** & How to mark them?
- A **negative weight cycle** is a cycle *whose total edge weight is negative*
- When there are negative weight cycles and its reachable to the start vertex, we couldn't find a shortest path. (we can always find a smaller path as long as we keep lopping in the cycle)
>[!Tip] If a negative weight cycle is reachable from the start vertex, then we want to mark it:
>>- All vertices on the cycle get distance $-\infty$
>>- All vertices reachable from the cycle get distance $-\infty$ too. 

So, the Bellman Ford is trying to detect those negative weight cycle through running the [[Introduction to Single Source Shortest Paths#The Generic SSSP Algorithm]] and using the arbitrary order (maybe in alphabetical order)：


# Generic Algorithm on G = (V, E)
```
SSSPInitialize(G,s)
	for all v
		v.d=infty
		v.p=nil
	s.d=0
Relax(u->v)
	if(u.d + weight(u->v) <v.d)
		v.d = u.d + weight(u->v)
		v.p = u

SSSP(G,s)
	SSSPInitialize(G,s)
	for(i = 1 to |V|-1) //this nested for loop goes through all layers in the graph to relax all edges
		for e(u->v) in all edges
			Relax(e)
	for e(u->v) in all edges // check for negative cycles
		if(u.d + weight(u->v) < v.d)
			v.d = -infty
			v.p = u
	for(i = 2 to |V|-1)
		for e(u->v) in all edges
			Relax(e)
```

# Analysis
- Initialization: $Θ(|V|)$
- Body: 2|V| - 2 rounds through |E| edges
- Total runtime:  $Θ(|V|*|E|)$

# Optimizations
## 1. Shortcut
## 2. Preprocessing

---
# Examples
[[Bellman Ford SSSP.excalidraw]]

|          | A   | B   | C   | D   | E   | F   | G   | S(Start) |
| -------- | --- | --- | --- | --- | --- | --- | --- | -------- |
| A        |     | 1   |     |     |     |     |     |          |
| B        |     |     | -2  |     | -5  |     |     |          |
| C        |     |     |     | 5   |     |     |     |          |
| D        |     | -3  |     |     |     |     |     |          |
| E        | 5   |     |     |     |     | -1  | 3   |          |
| F        |     |     |     |     | 2   |     | 8   |          |
| G        |     | 7   |     |     |     |     |     |          |
| S(Start) |     |     |     |     | 5   | 1   | 3   |          |

Bellman Ford algorithm with each vertex‘s shortest path from start and its descendant after every round

|     | 1st round | 2nd round | 3rd round | 4th round | 5th roud |
| --- | --------- | --------- | --------- | --------- | -------- |
| A   | -         | 10, E     | 8, E      |           | -        |
| B   | -         | 10, G     |           | 9, A      | -        |
| C   | -         |           | 8, B      | 7, B      | -        |
| D   | -         |           | 13, C     | 12, C     | -        |
| E   | 5, S      | 3, F      | -         |           | -        |
| F   | 1, S      | 1, S      | -         |           | -        |
| G   | 3, S      | 3, S      | -         |           | -        |
| S   | -         | -         | -         |           | -        |
|     |           |           |           |           |          |


---

