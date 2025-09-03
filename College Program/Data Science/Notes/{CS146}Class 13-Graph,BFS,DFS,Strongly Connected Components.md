---
create date: 2024-03-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - CS
  - CS/DataStructure
  - "#review"
modification date: 2024-03-09T17:47:00
type: CourseNotes
sr-due: 2024-04-01
sr-interval: 7
sr-ease: 186
---
# Before the Class
## Lectures and Materials
[[《2009 Introduction to Algorithms Third Ed》.pdf]] 
- Appendix: B.4 (p.1168~1172) 
- Ch 22.1 (p.589) - 22.3 
- [[Introduction to Graph]]
- [Video Lists](https://www.youtube.com/playlist?list=PLSVu1-lON6LyvT8iceopuqnmSmPiSA6wX)
- [Video: Kosaraju's Algorithm for Strongly Connected Components](https://www.youtube.com/watch?v=HOOmetF56BI)
---
# Review List
>[!Abstract] Topics
>1. BFS
>	- ResetGraph takes $Θ(|V|)$
>	- Let $V^\prime, E^\prime$ be the vertices and edges reachable from the start vertex.
>	- $Θ(|V^\prime|)$ vertives discovered, enqueued and dequeued
>	- $Θ(|E^\prime|)$ edges explored y dequeued vertices
>	- Total runtime: $Θ(|V|+|E^\prime|)$
>1. DFS
>	1. Runtime （For a $G=(V,E)$:）
>	- On a graph, takes time $Θ(|V|+|E|)$
>	- On a single vertex, with $G^\prime=(V^\prime,E^\prime)$, reachable from that vertex, takes time $Θ(|V|+|E^\prime|)$

---
## BFS (Breadth First Search)
[[Graphs-BFS(Breadth-First Search)]]

---
## DFS (Depth First Search)
[[Graphs-DFS(Depth-First Search)]]

---
## Strongly Connected Component
1. DFS topological sort
2. Do DFS again in topological sorted order after 1
# In-Class Problems
>[!question]
>1. You are given a directed graph, in adjacency list format:  the graph has an array of vertices, and each vertex contains an unordered Arraylist of vertices that that vertex has an edge to.  Assuming it is coded well, how long do each of the following computations take?  There are n vertices and m edges total.
>>[!answer]
>>1. Computing the outdegree of a vertex at index i takes time Θ(1)
>>2. Computing the outdegree of all vertices takes time Θ(n)
>>3. Computing the indegree of a vertex at index i takes time Θ(m+n)
>>4. Computing the indegree of all vertices takes time Θ(m+n)

>[!question]
>2. The time needed to compute $G^T$ given $G$ is:
>>[!Answer]
>>1. $Θ(n^2)$ if G is given as an adjacency matrix
>>2. $Θ(m+n)$ if G is given as an adjacency list

>[!question]
>3. You are running DFS on a **directed graph**, and you freeze time for a moment.  Imagine that there is an edge in the graph, and it currently goes from a vertex that is {white, gray, black} to a vertex that is {white, gray, black}.  By the end of the algorithm, the edge will eventually be categorized, as a Back edge, Cross edge, Forward edge, or Tree edge.  For each color pair in the table below, give a string for the possibilities.
>>| From/To | Whilte | Gray | Black |
| ------- | ------ | ---- | ----- |
| White   | BCFT   | BC   | C     |
| Gray    | FT     | BFT  | CFT   |
| Blcak   | None   | B    | BCFT  |


>[!question]
>3. You are running DFS on an **undirected** graph, and you freeze time for a moment.  Imagine that there is an edge in the graph, and it currently goes from the vertex you are at which is {white, gray, black} and to vertex that is {white, gray, black}.  (The graph is undirected, so "from" and "to" here are defined by the vertex you are currently at in the search.)  By the end of the algorithm, the edge will eventually be categorized, as a Back edge, Cross edge, Forward edge, or Tree edge.  For each color pair in the table below, a string for the possibilities.
>>| From/To | Whilte | Gray | Black |
| ------- | ------ | ---- | ----- |
| White   | BT   | B   | NONE     |
| Gray    | T     | BT  | T   |
| Blcak   | None   | B    | BT  |

---
## 1. Topological Sorting Problem
>[!Question] Find how many semester and what course should be chosen for a given list of course with prerequisite

---
## 2. How to model "prerequisite" and "co-requisite course" in graph
Using weigh to represent "how many semester you need to take before take this"

---
# Flash Cards
#flashcards/CS/datastructure
What is *vertex*, *edge*, *length*, *degree* and *reachable* in *graph*
???
**Vertex** is a node
**Edge** connect two vertices
**Length** is the number of edges in a path
**degree** is the edge count for a vertex
**reachable** means a path goes from one vertex to another
<!--SR:!2024-09-18,1,250-->

What is *directed (digraphs)* and *undirected graphs*
???
**digraphs**: all edges in graph only go one way
**undirect graphs**: all edges go both ways
<!--SR:!2024-07-14,89,290-->

What is *cycle*, *simple cycle*, *simple path* in graph
???
**cycle** is a path back to it start vertex
**simple cycle**:  only contains 1 cycle, itself
**simple path**: contains no cycle
<!--SR:!2024-07-08,83,270-->

What is *acyclic graph*, *DAG*, *weighted graph*?
???
**acyclic graph**: contains no cycles
**DAG**: directed acyclic graph
**weighted graph**: each edge has an associated weight depending it modeling
<!--SR:!2024-08-18,116,290-->

What is *in-degree* and *out-degree*?
???
**in-degree**: the number of directed edges pointing to a vertex
**out-degree**: the number of directed edges pointing from a vertex
<!--SR:!2024-10-03,16,230-->