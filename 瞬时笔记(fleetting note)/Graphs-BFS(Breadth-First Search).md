---
create date: 2024-03-21
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
  - CS/DataStructure/Graphs
modification date: 2024-03-21T09:24:00
type: LearningNote
sr-due: 2024-03-24
sr-interval: 3
sr-ease: 130
---

# Background & Materials
[[Introduction to Graph]]
[[《2009 Introduction to Algorithms Third Ed》.pdf]]
1. Ch 22.2 (p.589)
![Graphs: Breadth First Search (BFS) with Example](https://www.youtube.com/watch?v=ls4cHglfc0g&list=PLSVu1-lON6LxCmXNMfZBq7bdMAvUf3Sc7&index=3)
---
# Implementation
>[!note] Algorithm concept（Start from the startVertex） 
>> Search systematically explores the edges of G to discover every vertex that is reachable from start
```psudocode
ResetGraph(G)
	for v : V
		v.discovered = False
		v.dist = null;
		v.p = nil

BFS(G, startVertex)
	ResetGraph(G)
	startVertex.discovered = True
	startVertex.dist = 0
	Q = new Queue()
	Q.enqueue(startVertex)
	while(not Q.isEmpty())
		u=Q.dequeue()
		for each v such that u -> v
			if(not v.discovered)
				v.discovered = True;
				v.dist = u.dist+1
				v.p = u
				Q.enqueue(v)
```
# Analysis
- ResetGraph takes $Θ(|V|)$
- Let $V^\prime, E^\prime$ be the vertices and edges reachable from the start vertex.
	- $Θ(|V^\prime|)$ vertives discovered, enqueued and dequeued
	- $Θ(|E^\prime|)$ edges explored y dequeued vertices
-  Total runtime: $Θ(|V|+|E^\prime|)$ or $O(|V|+|E|)$ **Linear**
# Breadth-first trees
**predecessor subgraph of G**: ![[Pasted image 20240321100332.png|300]]
 >After procedure BFS we can get a $G_\pi$ is a breadth-first tree in which contain a unique path from s to v that is also a shortest path from s to v in G.

---
# Flash Cards
