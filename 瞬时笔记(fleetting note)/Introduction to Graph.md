---
create date: 2024-03-21
tags:
  - review
  - CS
  - CS/Algorithm
  - CS/DataStructure
  - 程序员
  - CS/DataStructure/Graphs
modification date: 2024-03-21T08:39:00
type: LearningNote
sr-due: 2024-03-24
sr-interval: 3
sr-ease: 250
---

# Background & Materials
>[!quote] background
>> - Matrix
>> - List

- [[《2009 Introduction to Algorithms Third Ed》.pdf]]
	1. Appendix: B.4 (p.1168~1172)
	2. Ch 22.1 (p.589)
- [Video: Introduction to Graphs](https://www.youtube.com/watch?v=Pdk8U1r7qvk&list=PLSVu1-lON6LxCmXNMfZBq7bdMAvUf3Sc7&index=2)
- [Video: Graphs: Representation](https://www.youtube.com/watch?v=WQ2Tzlxl_Xo&list=PLSVu1-lON6LxCmXNMfZBq7bdMAvUf3Sc7&index=2)

---
# Introduction to Graphs
## Basic Concepts
- **Graph**: A set of **Vertices** and a set of **Edges**
	- **Vertex (or Node)**
	- **Edge**: connects two vertices. Represent relation between those things
- **adjacent vertices** share an edge
- An edge is **incident** on its vertices
- A vertex's **neighbors** are the vertices adjacent to it.
- Vertices in sequence connected by edges from a **path**.
- The number of edges in a path is the path's **length**.
- The edge count for a vertex is its **degree**.
- If a path goes from one vertex to another, the latter is **reachable** from the first.
- All edges in **undirected graphs** go both ways.
- Edges in **directed graphs (digraphs)** go one way.
- A **cycle** is a path back to its start vertex.
- A **simple cycle** contains no other cycles.
- A **simple path** contains no cycles.
- An **acyclic graph** contains no cycles.
- A **DAG** is a directed acyclic graph
- The number of directed edges pointing to a vertex is its **in-degree**.
- The number of directed edges pointing from a vertex is its **out-degree**.
- In a **weighted graph**, each edge has an associated weight.
---
# 2 Representations of Graph
## 1. Adjacency-List
![[Pasted image 20240309204105.png|600]]
## 2. Adjacency-Matrix
![[Pasted image 20240309203740.png|600]]
For undirected graphs:
![[Pasted image 20240309203858.png|600]]
## Comparisons
### Memory(Space)
- Adjacency *List*：$Θ(|V|+|E|)$
- Adjacency *Matrix*：$Θ(|V|^2)$
### Functions
1. Iterate through neighbors of a vertex i
	1. Adjacency List：$Θ(outdegree(i))$
	2. Adjacency Matrix：$Θ(|V|)$
2. Check for edge(i, j)
	1. Adjacency List：
		1. Linked List or Unsorted Array：   $O(outdegree(i))$
		2. Sorted Array or Tree：$O(lg^{outdegree(i))})$
	2. Adjacency Matrix：$Θ(1)$
### Some algorithms
1. Outgoing List to Incoming list
2. Incoming List to out-going List
3. Adjacency list to matrix 
4. Graph transpose(reversing all edges in a graph)
## Representing attributes
Most algorithms that operate on graphs need to maintain attributes for vertices and edges.
There are many ways to implement it in different real programing languages. Such as: 
- Using additional array to store those attributes
- Represent them as instance variables within a subclass of  a vertex class
---
# D.1 Matrices and matrix operations
### Matrices and vectors
A **matrix** is a rectangular array of numbers:
![[Pasted image 20240309193622.png|1100]]
The **transpose** of a matrix A is the matrix $A^T$ obtained by exchanging the rows and colums
A **vector** is a one-dimentional array of numbers. 
The **unit vector** $e_i$ is the vector whose ith element is 1 and all of whose other elements are 0.
A **zero matrix** $e_0$ is a matrix all of whose entries are 0.
##### Square matrices
1. **diagonal matrix:** $a_ij=0$ whenever $i！=j$ 
2. **identity matrix** $I_n=diag(1,1,...,1)$
3. **tridiagonal matrix**: T is one for which $t_ij=0$ if $|i-j|>1$
4. **upper-triangular matrix**: U is one for which $u_(ij)=0$ if i >j
5. **lower-triangular matrix**: L is one for which $l_ij=0$ if i < j
6. **permutation matrix**: P has exactly one 1 in each row or colum and 0 else where
7. **symmetric matrix**: A $A=A^T
##### Basic matrix operations
1. **matrix addition / subtraction**
2. **scalar multiple**
3. **matrix multiplication**: If $A=(a_ik)$ is an m * n matrix and $B=(b_kj)$ is an n * p matrix, then their matrix product C=AB is the $m * p$ matrix $C=c_ij$, where $c_ij=a_ikb_kj$
---
# Flash Cards
