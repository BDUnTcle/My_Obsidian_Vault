---
create date: 2024-04-01
tags:
  - review
modification date: 
type: LearningNote
sr-due: 2024-04-07
sr-interval: 2
sr-ease: 245
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[Introduction to Graph]]
- [[Graphs-DFS(Depth-First Search)]]
[Video: Topological Order and Topological Sorting](https://www.youtube.com/playlist?list=PLSVu1-lON6LyvT8iceopuqnmSmPiSA6wX)

---
# Basic Concepts
## Fully Ordered Sets and Partially Ordered Sets
- **Fully Ordered Sets** refers to those set whose values can be easily ordered by some math rules, like *15<30*. Usually, those components can easily denoted by numbers.
- **Partially Ordered Sets** refers to sets that its components has *somehow* ordering like you need do Job 1 before Job 2, here we denote it as *Job 1 < Job 2* here. Usually, those components could not easily described by a single number, but more realistic things, like job, course and etc..
>[!important] Topological representation in Graph to describe partially ordered sets
>> If there is a directed acyclic graph in which all vertices are in a line with all edges outcoming from left to right, we say that's a topological ordering graph
>> ![[Pasted image 20240405180314.png|700]]
# Kahn's Algorithm
[[Kahn's Algorithm]]
# DFS for Topological Sort
[[DFS Based Topological Sort]]

---
# Flash Cards & Review List
1. Fully Ordered Sets and Partially Ordered Sets concepts
2. Topological ordering graph
3. 2 algorithms about topological sorting (Kahns, DFS)