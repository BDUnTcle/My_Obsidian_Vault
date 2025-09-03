---
create date: 2024-03-25
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
  - CS/Algorithm/ShortestPath
modification date: 2024-03-25T07:56:00
type: LearningNote
sr-due: 2024-03-29
sr-interval: 2
sr-ease: 229
---

# Background & Materials
[Single Source Shortest Paths](https://www.youtube.com/playlist?list=PLSVu1-lON6LyvJV6EwIJrcZi4ONJmQCQ5)

---
# What is Shortest Paths and Shortest Path Trees
If you fun a [[Graphs-BFS(Breadth-First Search)]], and <mark style="background: #ABF7F7A6;">If the weight of all edge are 1</mark>, in each phase, you could get a set of shortest path from vertex x from the start vertex. At the end of it, you will get a shortest path tree. So you could:
1. Use *d* to store the number of links to reach a vertex
2. Use *p* to store the predecessor vertex used on the path of length *d*
When there are different weights, we could do it similarly:
1. Use *d* to store <mark style="background: #FF5582A6;">an upper-bound distance estimate</mark> to reach a vertex
2. Use *p* to store the predecessor vertex used on the path of length *d*
```
SSSPInitialize(G,s)
	for all v in V
		v.d = ∞
		v.p = NIL
	s.d = 0
```
```
FindPath(s,v)
	if(v == s)
		return new List().add(v)
	if(v.p == NIL)
		return nil
	return FindPath(s,v.p).add(v)
```
# Relaxing a edge
For start vertex s:
1. If you find a path from *s* to *u* of total weight *x*, the shortest path from *s* to *u* has weight no more than *x*
2. If there is a path from *s* to *u* of total weight *x*, and an edge from u->v of weight *y*, there is a path from *s* to *v* of total weight weight *x+y*
```
Relax(u,v)
	if(u.d + weight(u->v) < v.d)
		v.d = u.d + weight(u->v)
		v.p = u
```
# The Generic SSSP Algorithm
```
SSSP(G,s)
	SSSPInitialize(G,s)
	for each edge e in G(possibly repeating edges) in some order
		Relax(e)
```
- At completion, no further edge relaxation would change any distance
- The sequence of relaxations must **contain a critical edge ordering**
## Critical edge ordering concept
An ordering that contains edges from a shortest path to **each** vertex from the start vertex
The **critical edge ordering** gives us an constrain that makes sure we find the correct shortest edge, so whatever order one SSSP algorithm use, it must follow the ordering (but the actual order maybe various)
So, to show an SSSP algorithm is correct, the only thing we need to do is to show the algorithm follows this basic form, and that somewhere in its entire sequence of relaxations you can prove that it will always relax some critical ordering.

---
# Review List
1. What is [[#Relaxing a edge]]?
2. [[#The Generic SSSP Algorithm]]
3. Why [[#Critical edge ordering concept]] is critical for a SSSP algorithm?


---
# Flash Cards
