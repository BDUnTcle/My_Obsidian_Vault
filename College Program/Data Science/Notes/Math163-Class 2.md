---
create date: 2024-09-03
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math163_Lecture01.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Basic Combinatorics concepts and theories
>	1. [[#The Basic Counting Principle]]
>	2. [[#The generalized principle of counting]]
>2. [[#Permutation & Combination]]



---
# In-Class Problems
## The Basic Counting Principle
![[Math163_Lecture01.pdf#page=1&rect=69,554,501,615|Math163_Lecture01, p.1]]

---
## The generalized principle of counting
![[Math163_Lecture01.pdf#page=1&rect=71,457,501,547|Math163_Lecture01, p.1]]
## Permutation & Combination
![[Math163_Lecture01.pdf#page=1&rect=68,174,501,287|Math163_Lecture01, p.1]] 
>[!question] The "PEPPER" problem
>> $\frac{6!}{3!2!}$ where the $3!$ represent the 3 identical "P", and the $2!$ represent the 2 identical "E"

^90718e
![[Math163_Lecture01.pdf#page=2&rect=68,611,504,720|Math163_Lecture01, p.2]]
> [!PDF|red] [[Math163_Lecture01.pdf#page=2&selection=114,0,117,39&color=red|Math163_Lecture01, p.2]]
> >[!faq] Consider a set of 12 antennas of which 4 are defective and 8 are functional. Assume that all the defective antennas and all the functional antennas are indistinguishable from each other. How many linear orderings are there in which no two defective antennas are consecutive?
> > A: $\binom{9}{4}$
> >>[!tip] think to insert 4 number into the slots of 8 numbers
> >>> ![[Excalidraw/Drawing 2024-09-23 19.00.19.excalidraw.md#^area=MrMjdUTDGNtNbJAelakA6]]
> >> here, n=8 , r=4. So there are 8+1 slots for 4 identical object.
 
> [!PDF|red] [[Math163_Lecture01.pdf#page=2&selection=121,0,131,41&color=red|Math163_Lecture01, p.2]]
> >[!faq] Consider n-digit numbers where each digit is one of the integers 0, 1, . . . , 9. How much such numbers are there for which
> >a. no two consecutive digits are equal?
>> A: $10*9^{n-1}$
>> b. 0 appears as a digit a total of i times, i = 0, . . . , n
>> A: $\binom{n}{i}9^{n-i}$

![[Math163_Lecture01.pdf#page=3&rect=66,292,416,382&color=red|Math163_Lecture01, p.3]]
>[!tip]
>Consider the scenario that a set of n different objects where one of them are *special*. Now want to choose r object from n.
>Then the all possible outcome is $\binom{n}{r}$, clearly.
> But it could also to think like this: 
>> The event divided into 2 part A and B where:
>> A: Choose r objects from n which must contain the special card. Its $\binom{n-1}{r-1}$, because the special one must to be choose, only need to choose r-1 from n-1
>> B: Choose r objects from n without the special one. Its $\binom{n-1}{r}$, because we can not choose the special one, so only n-1 objects.

---

# Flash Cards
#flashcards/Math
Why  $\binom{n}{r}=\binom{n-1}{r-1}+\binom{n-1}{r}$?
???
Think about **A set of n different objects where one of them are *special*. Now want to choose r object from n.**
<!--SR:!2024-10-09,7,250-->

$\binom{n}{r}=?$ <--->$?=\frac{n!}{r!(n-r)!}$
<!--SR:!2024-10-15,13,270!2024-10-12,10,270-->