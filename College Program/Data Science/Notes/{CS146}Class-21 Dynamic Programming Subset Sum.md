---
create date: 2024-04-14
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - CS
  - CS/Algorithm
  - 程序员
modification date: 
type: CourseNotes
---
# Before the Class
## Lectures and Materials
- [[Subset Sum Problem]]
- [Videos: Dynamic Programming](https://www.youtube.com/playlist?list=PLSVu1-lON6LwaLkn1J4slNQEp2oEjWCqX)
- [[{CS146}Class-21.excalidraw]]
---
# Review List
>[! abstract] Main Topics
>1. 

---
# In-Class Problems
## About Program 3
2 algorithms for topological sorting, compare them and find the best one

## Longest increasing subsequence
>Given a sequence of integers
>Looking for the longest increasing subsequence

```
if use LIS (S, i) represent the length of longest increasing subsequence in S{1,..., i} ending with S[i]
LIS(S,i)
{
	if(i<0) return 0
	ans =1
	for(j=0 to i-1)
		if(seq[j]<seq[i])
			ans=Max(ans,1+LIS(S,j))
}
takes O(n^2)
if use LIS(S,i,limit) represent the longest increasing seq in S{0,...,i}which has all values < limit
```
### Optimization
- Keep tracing the best subsequence through the process and use binary sort->(O (nlogn))
# Example of Floyd-Warshall
![[Pasted image 20240507183037.png]]

| D3  | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| 1   | 0   | 3   | 9   | 3   |
| 2   | 4   | 6   | 6   | 2   |
| 3   | 4   | 3   | 0   | 1   |
| 4   | 1   | 3   | -7  | 0   |

| D4  | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| 1   |     |     | -4  |     |
| 2   | 3   | 5   | -5  |     |
| 3   | 2   |     | -6  |     |
| 4   |     |     |     |     |

| Π3  | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| 1   | -   | 3   | 7   | 1   |
| 2   | 4   | -   | 6   | -4  |
| 3   | 17  | 3   | -   | 2   |
| 4   | 9   | 3   | 7   | -   |

| Π4  | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| 1   |     |     | 7   |     |
| 2   | 9   | 3   | 7   |     |
| 3   | 9   |     | 7   |     |
| 4   |     |     |     |     |


---

# Flash Cards
