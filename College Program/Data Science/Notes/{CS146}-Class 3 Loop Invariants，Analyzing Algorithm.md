---
create date: 2024-03-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - CS/Algorithm
  - review
modification date: 2024-03-09T17:58:00
type: CourseNotes
sr-due: 2024-04-20
sr-interval: 23
sr-ease: 250
---
# Before the Class
## Lectures and Materials
- [[CS-146 Sec 05 - Data Structures and Algorithms]]
- [[《2009 Introduction to Algorithms Third Ed》.pdf]] 
	- Chapter 2 (p.16)
- [Video: Loop Invariants](https://www.youtube.com/watch?v=3YP6NP1_tF0)
- [Video: Conversion to Binary](https://www.youtube.com/watch?v=K_zZZ_cgJF8)
---
# Review List
>[!Abstract] Topics
>Ch 2.1 (p.16~23)
>>1. The definition of **Loop Invariant**: properties which work for each iteration in a loop of an algorithm
>>2. Loop invariants is used to understand why algorithm is correct
>>3. 3 things about a loop invariant
>>	1. Initialization: show that the algorithm correctness at the start of loop 
>>	2. Maintenance: show that the algorithm correctness during every iteration of loop
>>	3. Termination: show that the algorithm correctness at the end of loop
>
>Ch 2.2 (p.23)
>>1. Basic rules in program algorithm analyzing (RAM model)
>>	1. Instructions which take **constant time**: arithmetic (+-*/...), data movement (load, store, copy), control 
>>	2. Think execute each line of pseudocode takes **constant time**
>>2. Step of analyzing for a algorithm runtime (p.26)
>>	1. .why the insertion sort takes quadratic time at the worst case ?
>>	2. Worst-case and averrage-case analysis
>>3. What is **order of growth (rate of growth)**: Θ() notation

- [[#2.1 Introduction to Loop Invariants & insertion sort]]
- 
---
# In-Class Problems
### 2.1 Introduction to Loop Invariants & insertion sort
- Why we learn it？
	- To make sure your alg really works
	- Help you to understand debugging
- How to proceed a loop invariant
	- Follow the program
	- Try to prove your loop invariants
>[!tldr] Procedure in Loop Invariant Proof
>1. Find the Loop Invariant 
>	1. State the location of loop invariant (different location will give different loop invariant)
>	2. Find the range of variables (like i)
>	3. State what the loop do
>>2. Proof it holds for initialization
>>3. Proof it holds for maintenance
>	1. Try to find relationship of variables between current iteration i and next iteration $i^\prime$
>	2. Using reference from the code and compare 2 iteration, proof it holds
>>4. Proof it holds for termination
>	1. 
- Pseudocode of insertion sort
![[Pasted image 20240315091943.png|800]]
### Loop Invariant Practice Promblem
![[Pasted image 20240506034723.png|1000]]
>[!note]
>>The loop invariant is : for integer $0\leq j<\frac{i}{2}$, $A[2j]=A[i]=n$
>>The loop exit condition is: i=A.length+2
>>Initialization: $i=0$, $j=0$ $A[0]=n$ holds
>>Maintenance: 
>>let the next iteration of $j$, $A[j]$ to be $j^\prime$, $A^\prime[j^\prime]$
>> $j^\prime=j+2$, $A^\prime[j]=A[j+2]=n$
>> $i^\prime=i+2$, $A^\prime[i]=A^\prime[j]=n$
>>
### 2.2 Analyzing Algorith m
- Input size
- Runnning time
#### Analysis of insertion sort
#### The order of growth
- Ignore lower order terms and the leading term‘s constant coefficient
### Conversion to binary

## Assignment after Class
---
# Flash Cards