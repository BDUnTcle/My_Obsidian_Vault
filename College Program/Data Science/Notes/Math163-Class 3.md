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
$$
\int \limits_{0}^{\infty}xe^{-x(1+a)}dx 
$$
---
# Review List
>[! abstract] Main Topics
>1. [[#The Binomial Theorem]]
>2. The multinomial coefficients & multinomial theorem
>3. Stirling's Formular

---
# In-Class Problems
## The Binomial Theorem
![[Math163_Lecture01.pdf#page=3&rect=70,67,451,142|Math163_Lecture01, p.3]]
### Proof for the binomial theorem
### Practice problems
> [!PDF|red] [[Math163_Lecture01.pdf#page=4&selection=14,0,18,18&color=red|Math163_Lecture01, p.4]]
> >[!faq] How many subsets are there of a set of n distinct elements?
>- $2^n$ if allow the empty set
>- $2^n-1$ if not allow the empty set

---
## Multinomial Coefficients
- ? In how many ways can $n$ objects be divided into $r$ groups of size $n_{1},n_{2},\dots,n_{r} \left( \text{with} \sum\limits_{i=1}^{r}n_{i}=n \right)$

![[Math163_Lecture01.pdf#page=5&rect=64,635,455,721|Math163_Lecture01, p.5]]
### Practice problems
> [!PDF|red] [[Math163_Lecture01.pdf#page=4&selection=57,0,87,29&color=red|Math163_Lecture01, p.4]]
> >[!question] In how many different ways can n distinct objects (think balls labeled 1, 2, . . . , n) be placed into r baskets such that the first basket receives n 1 balls, the second n 2 balls etc.? We would count an arrangement as different only if two balls from different baskets were to be exchanged.
> For the basket 1: $\binom{n}{n_{1}}$
> For the basket 2: $\binom{n-n_{1}}{n_{2}}$
> For the basket 3: $\binom{n-n_{1}-n_{2}}{n_{3}}$
> ...
> For the basket r: $\binom{n-n_{1}-\dots-n_{r-1}}{n_{r}}$
> So the total possible outcome needs to product all of above, after simplifying we get the multinomial coefficient

> [!PDF|red] [[Math163_Lecture01.pdf#page=5&selection=72,0,75,34&color=red|Math163_Lecture01, p.5]]
> > You have twelve different toys which you want to give to three children so that the oldest child receives five toys, the middle child four and the youngest child three. In how many ways can that be done? What if the toys were indistinguishable (think 12 chocolate chip cookies)?
>>>[!info] For the different case, by using the multinomial coefficient:
> $n=12,n_{1}=5,n_{2}=4,n_{3}=3$
> \# = $\frac{12!}{5!4!3!}$
> 
> >>[!info] For the identical case: 12 same items divide into
> >> Since the cookies are indistinguishable, there is only **1 way** to distribute the cookies because we are distributing fixed numbers to each child and all cookies are the same.

## Multinomial Theorem
![[Math163_Lecture01.pdf#page=5&rect=70,332,499,444&color=red|Math163_Lecture01, p.5]]
### Practice problems
> [!PDF|red] [[Math163_Lecture01.pdf#page=5&selection=194,0,208,1&color=red|Math163_Lecture01, p.5]]
> > Expand $(x_{1} + x_{2} + x_{3})^3$

## Number of Integer Solutions of Equations
>[!faq] How many ways to distribute $n$ distinguishable balls into  $r$ distinguishable urns? Why?
>> $r^n$, Because for each n object, you have r choices to decide which urn to put
>>> [! tip] What if the urns are distinguishable but the balls all look the same?
>>> Look below


> [!PDF|red] [[Math163_Lecture01.pdf#page=6&selection=28,0,37,15&color=red|Math163_Lecture01, p.6]]
> >[! faq] In how many ways can n identical balls be distributed among r distinguishable urns?
> -  a.  $\binom{n+r-1}{r-1}$ for the case that its ok for urns to remain empty
> -  b.  $\binom{n-1}{r-1}$ for the case that every urn needs to receive at least one ball (in this case, $n\geq r$)
>>[!tip] For this problem, consider divide n balls into r different urns like insert "bars" between the gap of each balls.
>>- So if you want to divide n objects into r groups, just need to insert r-1 "bars" in between those n objects. Then we get a sequence with n+r-1 items where n items are the same and other r-1 items are also same. Then recall to the [[Math163-Class 2#^90718e|"PEPPER" Problem]] , we get $\binom{n+r-1}{r-1}$ for some urns could be empty.
>>- if we don't allowed urns to be empty, which means we can not insert "bars" either at the first and last slots or insert more than 2 "bars" into one slots. So that easily comes into choose n-1 from r-1, which is  $\binom{n-1}{r-1}$
>>


![[Math163_Lecture01.pdf#page=6&rect=66,85,503,205&color=red|Math163_Lecture01, p.6]]

## Stirling's Formula with proof
![[Math163_Lecture01.pdf#page=7&rect=67,538,456,643&color=red|Math163_Lecture01, p.7]]

---

# Flash Cards
#flashcards/Math
What is The Binomial Theorem
???
$$
(x+y)^n=\sum\limits_{k=0}^{n}\binom{n}{k}x^ky^{n-k}=\sum\limits_{k=0}^{n}\binom{n}{k}y^kx^{n-k}
$$
<!--SR:!2024-10-08,6,250-->

How many subsets are there of a set of n distinct elements?
???
- $2^n$ if allow the empty set
- $2^n-1$ if not allow the empty set
<!--SR:!2024-10-09,7,250-->

What is Multinomial Coefficients and Multinomial Theorem
???
To divide **n different objects** into **r different groups**
![[Math163_Lecture01.pdf#page=5&rect=64,635,455,721|Math163_Lecture01, p.5]]
![[Math163_Lecture01.pdf#page=5&rect=70,332,499,444&color=red|Math163_Lecture01, p.5]]
<!--SR:!2024-10-08,6,250-->

There are {{$\binom{n+r-1}{r-1}$}} **distinct non-negative (could be 0) integer-valued** vectors $(x_1, x_2,..., x_r)$ satisfying the equation $x_{1}+x_{2+\dots+x_{r}=n}$ There are {{$\binom{n-1}{r-1}$}} **distinct positive integer-valued** vectors $(x_1, x_2,..., x_r)$ satisfying the equation $x_{1}+x_{2}+\dots +x_{r}=n， r\leq n$
<!--SR:!2024-10-08,6,250!2024-10-09,7,250--> 