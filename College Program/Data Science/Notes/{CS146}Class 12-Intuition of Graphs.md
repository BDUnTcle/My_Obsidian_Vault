---
create date: 2024-03-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
modification date: 
type: CourseNotes
---
# Before the Class
## Lectures and Materials
1. [[《2009 Introduction to Algorithms Third Ed》.pdf]]
2. [Video: Graphs: Basics](https://www.youtube.com/playlist?list=PLSVu1-lON6LxCmXNMfZBq7bdMAvUf3Sc7)
3. [[Introduction to Graph]]

---
# Review List
>[!Abstract] Topics
>1. Basic concepts of graph: 
>	- vertices, edges, in/out-degree, direct/undirect graphs
>	- cycle, acyclic, DAG
>2. 2 ways in representations of graphs
>	1. Matrix
>	2. Lists

---
# In-Class Problems
## Problems
> Given n wrestlers, m rivalries, can you label each wrestler as "good guy" or "bad guy" such that every rivalry is between one of each
> You can get the rivalies' list：（1，7）（3，9）（14，7）（9，2）（1，14）。。。
> Rivalry can not happens to the same label
> Determine if it is possible
```
While（an unlabeled wrestler exist）
	1. label an unlabeled wrestler as Good
	2. propagate any constraints
	3. if contradiction，return fail
	4. no contradiction，next loop
return 
```
First get a graph of each wrestler and its opposite（bad or good）

## Heap 
When the extractMax () is called and the heap has 3 or 4 or all the same number, then call maxHeapify (), possiblely error happendsxHeapify (), possiblely error happends

---