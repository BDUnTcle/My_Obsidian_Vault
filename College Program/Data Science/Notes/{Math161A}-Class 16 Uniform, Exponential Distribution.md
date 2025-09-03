---
create date: 2024-03-19
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#flashcards"
  - review
  - Math
  - Math/Probability
modification date: 
type: CourseNotes
sr-due: 2024-03-24
sr-interval: 3
sr-ease: 250
---

[[#Review List]]
# Before the Class
## Lectures and Materials
[[Math161A_Lecture08.pdf]]
[[ContinuousDistributions.pdf]]

---
# In-Class Problems
## Uniform distribution
### Definition
>[!note] If the outcomes of a random variable are all numbers (e.g.,1,2,..., 6 for rolling a fair six-side die), then this distribution has a name: **discrete** Uniform distribution

>[!important] And the analogous continuous distribution is called the **continuous** Uniform distribution
>>We have to consider all possible values in an interval (a, b). 
>> The probability that X falls into a subinterval should only depend on the length of the subinterval (a, b)
> ![[Pasted image 20240321103631.png|900]]

>[!important] Notation, CDF, E (X) and V (X)
>>**1. Notation**: $X\sim Uniform(a,b)$
>>**2. CDF**：$F (x) = \begin{cases}  0 & \text{for } x < a,    \\\frac{x-a}{b-a} & \text{for } a \leq x \leq b,  \\1 & \text{for } x > b \end{cases}$
>>**3. $E(X)=\frac{a+b}{2}$**
>>**4. $E(X^2)=\frac{a^2+ab+b^2}{3}$**
>>**5. $V(X)=E(X^2)-E(X)^2=\frac{(b-a)^2}{12}$** 

## Exponential distribution
### Definition
>[!hint] Recall: The [[{Math161A}Class12-Geometric, Negative Binomial]] was used to model the number of independent Trials until (and including) the first success.

![[Pasted image 20240321105638.png|900]]
![[Pasted image 20240321105757.png|1000]]
### Features
>[!important] Survival Function
>![[Pasted image 20240321110131.png]]

>[!important] "Lack of memory" property
> ![[Pasted image 20240321190607.png]]

### E (X) and V (X)
![[Pasted image 20240321190453.png]]

---
# Review List
>[! abstract] Main Topics
>1. "The Gamma Trick"
>2. The discrete and continuous Uniform distribution, what is the PDF, CDF, E (X), V (X)
>	- What looks like about real uniform distribution problems? (Feature: fixed probability in a timespan)
>3. Exponential distribution, PDF, CDF, E (X), V (X)
>4. Survivor Function, how to find $\lambda$ 

---
# Flash Cards
