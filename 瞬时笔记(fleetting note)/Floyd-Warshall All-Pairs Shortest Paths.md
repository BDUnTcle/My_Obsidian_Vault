---
create date: 2024-04-07
tags:
  - review
  - 程序员
  - CS
  - CS/Algorithm
  - CS/Algorithm/ShortestPath
  - CS/DynamicProgramming
modification date: 
type: LearningNote
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[Introduction to Graph]]
- [Video: Floyd-Warshall All-Pairs Shortest Paths](https://www.youtube.com/watch?v=miJ88I43x4E&t=437s)
- [[All-Pairs Shortest Path.excalidraw]]
---
# Recursive Idea
Given：
- Weighted, directed or undirected graph, vertices from 1 to n
- Use adjacency matrix representation
>[!tip] Idea
>> For the i to j path, only allow intermediate vertices numbered 1 to k
>> Use $D^k[i][j]$  to denote shortest i to j distance using only vertices from {1,..., k}
>> - If don't use vertex k, $D^k[i][j]=D^{k-1}[i][j]$
>> - If use vertex k, $D^k[i][j]=D^{k-1}[i][k]+D^{k-1}[k][j]$
>> - For k>0 $D^k[i][j]=min(D^{k-1}[i][k]+D^{k-1}[k][j],D^{k-1}[i][j])$ (shorter one of above)
>> - Base case: for all i $D^{0}[i][i]=0$, for i $\neq$ j $D^{0}[i][j]=W[i][j]$ (a direct edge)
# Recursive Algorithm
```
ShortestPath(i,j,k,W)
{
	if(k==0){
		if(i==j)
			return 0
		return W[i][j]
	}
	return min(ShortestPath(i,j,k-1,W),ShortestPath(i,k,k-1,w)+ShortestPath(k,j,k-1,W))
}
```
>For one i, j: $T(k)=3T(k-1)+1$ = Θ($3^n$)
>For all i, j: Θ($n^23^n$)
 
---
# Flash Cards & Review List
1. How can we use the output of the Floyd-Warshall algorithm to detect the presence of a negative-weight cycle
	1. $D[i][i]$ is negative