---
create date: 2024-03-26
tags:
  - review
  - CS
  - CS/Algorithm
  - 程序员
modification date: 2024-03-26T08:05:00
type: LearningNote
sr-due: 2024-03-29
sr-interval: 3
sr-ease: 250
---

# Background & Materials
- [[Introduction to Dynamic Programming]]

![the Rod Cutting Problem](https://www.youtube.com/watch?v=re9rF9SqRFc&list=PLSVu1-lON6LwaLkn1J4slNQEp2oEjWCqX&index=2)

---
# Problem Definition
Given: n inch steel rod, prices by length.
Find: maximum amount you can get by cutting and selling it
Example: How should you cut your 8 inch rod to maximize its sale price:

| Length | Price |
| ------ | ----- |
| 1      | 2     |
| 2      | 5     |
| 3      | 9     |
| 4      | 10    |
| 5      | 12    |
| 6      | 13    |
| 7      | 15    |
| 8      | 16    |
# Recursive Solution Design
- Two rods, recursively solve each one.
	- For this approach, there are 2 parameters: both side of the rode
- One piece to sell whole and a remainder, recursively solve the remainder.
	- For this approach, there only 1 parameter: the remainder after each iteration
- The longest piece to sell and a remainder, recursively solve the remainder.
	- For this approach, there are 2 parameters: the remainder, the longest piece you can sell
>[!note] Here We use the 2 nd approach since it has simplest parameter
>> There is a question we need to figure it out:
>>>[!question] What is one length to sell? How long should the first part be?

<mark style="background: #FFB8EBA6;">At the beginning, we don't  need to figure out the optimal answer, just do it in a general i version and try to find all possible value:</mark>
- ~ Optimal(n)= Price[i] + Optimal(n-i)
```
RodCutting(length, Price[])
	if(length==0)
		return 0
	max = -infty
	for(i=1; i<length+1 ;i++)
		tmp = Price[i] + RodCutting(length -i, Price)
		if(tmp>max)
			max = tmp
	return max
```
**Similar to the Fibonacci problem, the pseudocode above has many repeated work during the whole process.**
The total possibilities of a length n rod is：$2^{n-1}$

# Memoized Version
>[!tip] Recursive Solution to Memoized Solution
>>Because during the whole recursion, there is only 1 changing parameter: the remain length, so there is only linear number of each different maximum price. So:
>- Store the maximum price of rod length n once its got during recursion
>- Before each recursive call, check if we have got the maximum price before, if we did, just take it from the table
>> The new version looks like this:
```
RC(length, Price[])
	allocate Table[0,1,...,n]= -infty
	Table[0]=0
	RodCutting(length,Price[],Table[])
RodCutting(length, Price[], Table[])
	if(Table[length] == -infty)
		for(i=1; i<length+1 ;i++)
			tmp = Price[i] + RodCutting(length -i, Price[], Table[])
			if(tmp>max)
				Table[length] = tmp
	return Table[length]
```
# Iterative Version
```
RodCutting(n, Price[])
	allocate Table[0,...,n]=0
	for(length=1; length<= n+1; length++)
		for(i=1; i< length+1; i++)
			tmp=Price[i] + Table[length-i]
			if(tmp>Table[length])
				Table[length] = tmp
	return Tabble[n];
```
- Runtime: $Θ(n^2)$
- Space: $Θ(n)$

---
# Flash Cards
