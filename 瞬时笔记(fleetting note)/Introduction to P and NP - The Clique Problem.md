---
create date: 2024-04-17
tags:
  - review
  - 程序员
  - CS
  - CS/Algorithm
modification date: 
type: LearningNote
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[{CS146}-Class 4 Asymptotic Notation]]
- Graph Basics
- [Video: Introduction to P and NP: The Clique Problem](https://www.youtube.com/watch?v=B801ZELDFZo&list=PLSVu1-lON6LytLlGHl3cxq_PrwQBlnEhm&index=1&t=1s)
- [Video: NP-Complete Reductions](https://www.youtube.com/watch?v=u5W32YxmnL8&list=PLSVu1-lON6LytLlGHl3cxq_PrwQBlnEhm&index=2)

---
# Some Definitions
- **Complete graph**: an undirected graph with an edge between every pair of vertices
- **Clique**: a complete graph which is a subgraph of some other graph
- **Independent Set**: Given a Graph(V, E) a set of vertices $X \in V$ such that E contains no edges between 2 vertices in X
- **Dominating Set**: A set of vertices that dominate all vertices in a graph
	- Dominate: a vertex dominate every vertex which is connected to it.
- **Vertex Cover**: A vertex cover is a set of vertices that covers all edges in the graph
	- Cover: A vertex covers all edges incident on itself.
# The complexity class P
>[!question] How to check if given graph G=(V, E) and some vertices $C\subseteq V$  is a clique?
>- Check those vertices, pair by pair, for edges.
>> This algorithm will take no more than $O(V^2)$ time no matter what kinds of form the graph use (adjacency matrix or list).
- **P (Polynomial)**:  if a decision (yes/no) problem of input size n can be solved in $O(n^c)$ time for any constant c, the problem is in the complexity class $p$
	- <mark style="background: #FFB86CA6;">The clique verification problem above is in p</mark>
# The complexity class NP
>[!question] A harder Question: Does a Given Graph=(V, E) have a clique of size k?
>Check each size k subset of V and check if it is a clique
>>- For fixed k: the algorithm runtime will be polynomial ($O(V^{k+2})$ for each subset)
>>- For growing size of k=V/2, $\binom{V}{k}=Θ(2^V/\sqrt(V))$, not polynomial

- **NP (Nondeterministic Polynomial)**: if for all yes instances of a decision problem of input size n, there exists a certificate that can be used prove it in $O(n^c)$ time for any constant c, the problem is in the complexity class NP 
> $P\subset NP$ and  $P\subset co-NP$ 

>[!tip] $x \in NP$ is a statement of ease

>[!note] NP,  NP-Hard and NP-Complete
## Decision Problems vs. Optimization Problems
We could use the solve of a decision problem to help us to solve the optimization problems
>[!question] Find the size of the largest clique in polynomial time 
>Find largest k such that G has a clique of sike k

>[!question] Find a clique of maximum size in polynomial time
>1. Find k, the maximum sized clique in the graph
>2. Remove a vertex from the graph, check if a size k clique still remains
>	1. If not, it means we need that vertex, just put it back and mark it as part of our clique
>	2. If yes, it means we don't need it anymore. Discard it forever
>3. Do phase 2 until we get a size k clique, or keep doing for all vertices
>> In this algorithm, there are $O(V)$ total calls to the Clique() which takes polynomial time
# NP Complete Reduction
>[!question] A basic independent set problem: Is there an independent set of a given graph?

The independent set problem could be solved by using clique, we call it as "*the independent set reduce to clique*" and the notation "*Independent set $\leq_p$ clique*" (the independent set problem isn't harder than the clique problem)
**For independent set problem and clique problem, its reversable, so we can also say** *clique* $\leq_p$ *Independent set*
## Vertex Cover Problem
### Definition
A vertex cover is a set of vertices that covers all edges in the graph
![[Pasted image 20240423211219.png|300]]
Here, the vertex 5, covers edge (5,6) (5,4) (5,3)
>[!question] if a graph have a vertex cover of given size k (k>0)?

---
# Flash Cards & Review List
