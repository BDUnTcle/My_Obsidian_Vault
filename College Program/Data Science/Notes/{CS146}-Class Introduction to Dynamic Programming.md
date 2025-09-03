---
create date: 2024-03-25
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
- [[Introduction to Dynamic Programming]]
- [Videos: Dynamic Programming](https://www.youtube.com/playlist?list=PLSVu1-lON6LwaLkn1J4slNQEp2oEjWCqX)
---
# Review List
>[! abstract] Main Topics
>1. Two ways in dynamic programming to calculate Fibonacci number
>2. The general steps in dynamic programming (5 steps)

---
# In-Class Problems
>[!note]  Idea behind dynamic programming
>> Do not do repeat work

Given a positive integer $X_0$, write a sequence X that:
$X_{i+1}=X_i/2$ if $X_i$ is even
$X_{i+1}=3X_i+1$ if $X_i$ is odd
Until $X_{i+1}$ hit 1
 Give a lower and upper bound, find for lower<=i<=upper the maximum X (i)(the length of the sequence)
```
L(n)
	List m = {n}
	if(i == 1) return 1
	if n is even
		m.add(n/2)
	else if n is odd
		m.add(3n+1)
```

---
# Flash Cards
