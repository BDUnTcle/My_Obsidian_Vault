---
create date: 2024-03-26
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
modification date: 2024-03-26T07:26:00
type: LearningNote
sr-due: 2024-03-29
sr-interval: 3
sr-ease: 250
---

# Background & Materials
- Recursion
---
# Calculate the Fibonacci number
```
Fib(n)
{
	if(n<2)
		return n
	return Fib(n-1) + Fib(n-2)
}
```
Look at the simple recursive call to find the n-th Fibonacci number
Although it works, but the runtime is slow. 
The runtime is : $\omega(2^{n/2})$ 
>Notice, in the recursive tree, there is a lot of redundant subtrees that do the same thing.
>So if we could *remember the value and use it during the following process*, we can improve the efficiency
![[Excalidraw/Introduction to Dynamic Programming.excalidraw.md#^area=QNq-8L-Xy54jQ0nKaQTtC|FibRecursionTree]]
## The memoized version of Fib
```
Fibonacci(n){
	Allocate Ans[0,1,...,n]=NIL
	Ans[0]=0
	Ans[1]=1
	return NewFib(n,Ans)
}
NewFib(n,Ans[]){
	if(Ans[n]==NIL)
		Ans[n]=NewFib(n-1,Ans) + NewFib(n-2,Ans)
	return Ans[n]
}
```
>The New Fib's runtime is $Θ(n)$
## The Iterative Algorithm of Fib
```
Fibonacci(n){
	Allocate Ans[0,1,...,n]=NIL
	Ans[0]=0
	Ans[1]=1
	for(i = 2;i<=n;i++)
		Ans[i]= Ans[i-2] + Ans[i-1]
	return Ans[n]
}
```
Rather than using recursion, the iterative version gives the other way to do it.
We could **optimize the memory efficiency** in here by using different strategies:
- Using a table Ans with capacity of 3 or 2

# Generic Steps in Dynamic Programming
1. Get recursive solution
2. Parameter Analysis
	1. How many distinct parameter combinations are there？
	2. Are there few enough to store answers for each combination of parameters?
3. Memoize
	1. Allocate a table to hold stored answers
	2. Before running recursive code, check if you have computed the answer
4. Move to iterative version
	1. For a given answer, what answers does it depend upon?
	2. Figure out order for indices to fill in answers after things they depend upon
5. Garnish
	1. Can you reuse space? Optimize for space
	2. Do you need to store extra information for a constructive answer?

---
# Flash Cards
