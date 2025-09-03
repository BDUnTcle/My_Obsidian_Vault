---
create date: 2024-03-25
tags:
  - review
  - CS
  - CS/Algorithm
  - CS/Algorithm/ShortestPath
  - 程序员
modification date: 2024-03-25T08:15:00
type: LearningNote
---

# Background & Materials
- Stack and Lists
- Graph Basics
- Topological Sorting
- [[Introduction to Single Source Shortest Paths]]
![Directed Acyclic Graph (DAG) Single Source Shortest Paths with Example](https://www.youtube.com/watch?v=ePqBaDRHkdk&t=1s)
# Review List
1. What kind of graphs could use this Algorithm to get the shortest path? (1 Constrain)
2. Why it works and why its correct (how to prove)
3. What a predecessor vertex really means during the process ?
4. Why topological order help us？
5. Why this algorithm may go wrong with cycles and how？
6. How fast of this algorithm？
>[!tldr]
>1. Step 1：Topological Sorting
>2. Step 2：keep updating shortest path from source vertex


---
>[!note] DAG Algorithm can Find shortest paths from a start vertex to all other vertices
>>1. Works on **weighted, directed acyclic Graphs**
>>2. Negative edge weights **Allowed**
>>3. Sufficient: No cycle reachable from start vertex
---
# Basic Idea
- We can get a random vertex v's shortest path to start by relax its **predecessor**（"predecessor" means a vertex u outgoing to v and the distance from start to u is shortest path）
- By calculate all vertices which outgoing to v in **topological order**, we could find the "predecessor" vertex
	- This works because the graph is **acyclic**
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

DAGSSSP(G,s)
	SSSPInitialize(G,s)
	for each u in V in topological order
		for edge e(u->v) outgoing from u
			Relax(e)
```
# Analysis
- Topological Sort：$O(|V|+|E|)$
- Loop through Vertices: $O(|V|)$
- Edge Relaxations: $O(|E|)$
- **Total**: $O(|V|+|E|)$
# Optimization
>Using topological order and check for negative cycles

```
SSSPInitialize(G,s)
	for all v
		v.d=infty
		v.p=nil
		v.discovered = false
		v.finished = false
	s.d=0
Relax(u->v)
	if(u.d+weight(u->v) < v.d)
		if(v.finished)
			fail
		v.d = u.d + weight(u->v)
		v.p = u
		
DAGSSSP(G,s)
	SSSPInitialize(G,s)
	vertList = TopOrder(G,s,List[])
	for each u in vertList in reverse order
		u.finished = true
		for edge e(u->v) outgoing from u
			Relax(e)

TopOrder(G,u,List[])
	u.discovered = true
	for edge e(u->v) outgoing from u
		if(v is not discovered)
			TopOder(G,v,vertList)
	append u to vertList
	return vertList
```

# Examples
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


---
