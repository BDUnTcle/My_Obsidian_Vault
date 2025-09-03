---
create date: 2024-03-19
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - CS/Algorithm
  - CS
modification date: 
type: CourseNotes
---
# Before the Class
## Lectures and Materials
- [[《2009 Introduction to Algorithms Third Ed》.pdf]] Ch 23 (p.624-642)
- [Videos: Minimum Spanning Trees](https://www.youtube.com/playlist?list=PLSVu1-lON6LzeG6cBYLnI4rf09zGkUvQ9)
- [Video: Kosaraju's Algorithm for Strongly Connected Components](https://www.youtube.com/watch?v=HOOmetF56BI)
[[Drawing 2024-03-19 21.28.01.excalidraw]]

---
# Review List
>[! abstract] Main Topics
>Generic Algorithm
>>[!note] Kruskal's algorithm with disjoint set data structure
>>1. Step 1: sorting edges
>>2. Step 2: walk through sorted edges
>>Runtime: $Θ()$
>
>>[!note] Boruvka's algorithm
>>- **component** in graph
>> Using different phases to find MST
>> Find smallest outgoing edges from every component in each phase 
>> Runtime: $Θ()$
>
>>[!note] Prim's algorithm
>>- has a source vertex "s"
>>- Using priority queue
>>- Runtime: $Θ()$



---
# In-Class Problems
## Definitions and assumptions
[Video: Introduction to Minimum Spanning Trees](https://www.youtube.com/playlist?list=PLSVu1-lON6LzeG6cBYLnI4rf09zGkUvQ9)
>[!question] Spanning Tree
>An **acyclic subset** T in an **undirected Graph** G, which connects all of the vertices
> ![[Pasted image 20240319094116.png|500]]

>[!question] Greedy Strategy, Safe edge, Cut, Crosses, light edge
>>[!note] The Greedy strategy is captured by following generic method, which grows the MST one edge at a time.
>So if we think like this: edge A is subset of the MST, we just keep find A and union the result with new A, finally we will get the MST. Such A is called **Safe edge**.
>- A **Cut (S, V-S)** of an undirected Graph is a partition of V like this:
> ![[Pasted image 20240319095605.png|600]]
> - We say that an edge **cross** the cut if one of its endpoints is in S and the other is in V-S
> - We say a cut **respects** a set A if no edge in A crosses the cut
> - A **light edge** crossing a cut if its weight is the minimum of any edge crossing the cut.

## A Theorem and its corollary
>[!important] 
>1. If (u, v) is a light edge, then edge (u, v) is safe for A. A is a subset of all edges and any cut respects A
>2. In a connected, undirected graph Graph G, A is a subset of E that included in some MST for G, C is a connected component in the forest G_A . If (u, v) is a light edge connecting C to some other component in G_A then (u, v) is safe for A.
## Algorithms of MST
>[!Abstract] The Generic Algorithms
>1. 
### Kruskal's algorithm
Using disjoint sets data structure
1. Sort all edges from smallest to the largest
2. Go through all edges in order and add edge into the MST if the vertex is not in any forest that we have found yet and also add edges that connect 2 forest and discard other edges
### Boruvka's algorithm
![Boruvka's algorithm](https://www.youtube.com/watch?v=bQga6WqLUvs&list=PLSVu1-lON6LzeG6cBYLnI4rf09zGkUvQ9&index=3&t=170s)
>[!Abstract] idea behind
>>1. Start with forest of single vertex "trees" spanning the graph 
>>2. The minimum weight edge incident on any vertex v is in the MST
>>3. The minimum weight edge with one vertex in forest tree $T_i$ is in the MST
>>4. One phase:
>>	1. Mark each $T_i$ tree of the forest
>>	2. Find the lightest edge leaving each $T_i$
>>	3. Add all of those edges to the forest

### Prim's algorithm
![Prim's algorithm](https://www.youtube.com/watch?v=BZb-ozM2PWo&list=PLSVu1-lON6LzeG6cBYLnI4rf09zGkUvQ9&index=4)
>[!Abstract] idea behind
>> 1. Start with a "special" (but arbitrary) vertex a, call it's forest tree $T_a$
>> 2. Add minimum weight edge between $T_a$ and the rest of the graph
>> 	1. Start from a, put other vertices in priority queue with edge weight from a 
>> 	2. Update all vertices and path weigh from a, then update the  priority queue
>> 	3. Pop up the first element in the queue, let it to be the new a ,then put the edge into the MST
>> 3. Keep doing 2 until $T_a$ covers the graph

dynamic programs and greedy algorithm
1. greedy algorithm: easy to come up with but hard to prove
2. Dynamic programs: hard to come up with but easy to prove
## The shortest path
1. Assume that you find a path and no calculation error when you cal the path weight
2. How to prove your answer?
3. If you have a strategy, how to prove it in each step?

---
# Flash Cards
