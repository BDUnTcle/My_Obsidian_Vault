---
create date: 2024-03-21
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
  - CS/DataStructure/Graphs
modification date: 2024-03-21T20:01:00
type: LearningNote
sr-due: 2024-03-24
sr-interval: 3
sr-ease: 250
---

# Background & Materials
[[Introduction to Graph]]
[[《2009 Introduction to Algorithms Third Ed》.pdf]]
1. Ch 22.3 (p.603)
![Graphs: Depth First Search (DFS) with Example](https://www.youtube.com/watch?v=qH-mHxkoK0Q&list=PLSVu1-lON6LxCmXNMfZBq7bdMAvUf3Sc7&index=4)
[DFS Visualization](https://www.cs.usfca.edu/~galles/visualization/DFS.html)

---
# Implementation
>[!note] Algorithm intuition（Start from the startVertex） 
>1.  Search explores edges out of the most recently discovered vertex v that still has unexplored edges leaving it
>2. Once all of v's edges have been explored, the search "backtracks"
>3. Keep doing until all vertices that are reachable from the original source vertex
```psudocode
ResetGraph(G)
	for v : V
		v.discovered = -1
		v.finishing = -1

DFS(G,startVertex)
	ResetGraph(G)
	DFSVertex(startVertex)

DFSVertex(u)
	u.discovered = time++;
	for each v such that u -> v
		if(discovered < 0)
			DFSVertex(v)
	u.dinishing = time++;
```
>The edge classification:
- <mark style="background: #FF5582A6;">Tree Edges</mark>: parent to a child
	- Go to an undiscovered vertex
- <mark style="background: #CACFD9A6;">Back Edges</mark>: to an ancestor
	- To a discovered but unfinished vertex
- <mark style="background: #ADCCFFA6;">Forward Edges</mark>: to a non-child descendant
	- To a finished vertex discovered after the current vertex
- <mark style="background: #BBFABBA6;">Cross Edges</mark>: everything else
	- To a vertex finished before the current vertex discovery
**In undirected graphs: there is no Forward or Cross Edges** 
*Why?*
In the undirected scenario, we don't talk about forward or cross edges because the graph lacks direction; you can move back and forth between the vertices without a sense of "forward" progression or "crossing" over.
# Analysis
For a $G=(V,E)$:
- On a graph, takes time $Θ(|V|+|E|)$
- On a single vertex, with $G^\prime=(V^\prime,E^\prime)$, reachable from that vertex, takes time $Θ(|V|+|E^\prime|)$

---
# Flash Cards
