---
create date: 2024-04-05
tags:
  - review
  - 程序员
  - CS
  - CS/Algorithm
  - CS/DataStructure/Graphs
  - CS/Algorithm/ShortestPath
modification date: 
type: LearningNote
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[Introduction to Graph]]
- [[Topological Sorting]]
- [[{CS146}-Class 14 Topological Sorting,Kahn's Algorithm]]
---
![[{CS146}-Class 14 Topological Sorting,Kahn's Algorithm#Kahn's Algorithm]] 

>[!warning] Running kahn's in a graph with cycles
>> If you try to running this algorithm in a graph with cycles, it will return a set whose size are smaller than the graph
>> Because when there are cycles in the graph, the indegree for those vertices in cycles will never decrement to 0
>> So, if you want to check if the graph has cycle, just check the size at the end

---
# Flash Cards & Review List
1. Basic thoughts behind this algorithm
2. Some optimization
3. How to check if there is a cycle?
