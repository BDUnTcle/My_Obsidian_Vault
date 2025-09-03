---
create date: 2024-03-12
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#review"
  - CS/DataStructure
  - 程序员
  - CS
modification date: 
type: CourseNotes
---
# Before the Class
**Corman's Text Book：Chapter 6**
**Corman's Text Book：Appendix B.5.3**
## Lectures and Materials
- [Video: Introduction to Binary Heaps (MaxHeaps)](https://www.youtube.com/watch?v=WCm3TqScBM8)
- [Video: Linear Time BuildHeap](https://www.youtube.com/watch?v=MiyLo8adrWw)
- [Video: Heap Sort](https://www.youtube.com/watch?v=onlhnHpGgC4)
- [Video: Binary Heaps for Priority Queues](https://www.youtube.com/watch?v=-WEku8ZnynU)
---
# Review List
>[!tldr]
>>[!note] Max Heap
>>1. Property
>>2. Insertion, Deletion, Max Heapify
>>3. Linear time building
>
>>[!note] Heap Sort
>>1. Runtime: $θ(nlgn)$
>>2. Space: $θ(n)$



---
# In-Class Problems
## Heap & Binary-Heap Definition and Property
### Definition
- A **perfect balanced binary tree** where every non-leaf has exactly 2 children and all leaves are at the same level
### Property
- The parent node is at least as large as its children
[[2024-02-05]]
## Heap Representations
- Using a **Array** to store the heap by the order top to bottom, left to right of the tree
## Important Operations 
- **Find the root**
- **Insertion** (2 steps)
	1. Insert the new node to the end of the array
	2. Bubble it to the right place (by keep comparing it to its parent node)
- **Deletion the Root**(2 steps)
	1. *Swap* the root and the last leaf
	2. do *Max heapify* operation
- **Max Heapify**
	1. compare the root with it children, using the largest value of them as the new root
- **Build a Heap**
	1. Using insertion build, takes $Θ(nlgn)$
	2. Linear time Build
## Heap Sort
1. Build a Max heap
2. Delete the root until the heap is empty
---
# Flash Cards
