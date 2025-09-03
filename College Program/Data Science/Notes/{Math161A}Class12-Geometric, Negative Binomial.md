---
create date: 2024-03-05
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - Math/Probability
  - Math
  - review
type: CourseNotes
sr-due: 2024-04-13
sr-interval: 3
sr-ease: 250
---
# Before the Class
read **TextBook**：[[《Probability and Statistics for Engineering》.pdf]] 3.5
## Lectures and Materials
[[Math161A_Lecture06.pdf]]
[[DiscreteDistributions.pdf]]

> [!note] 3 step approach to solve the distribution problems
> >1. Define the random variables in words (X = # of ...)
> >2. State the specified distribution you use (X~<u>name</u> (parameter))
> >3. Solve the problems by calculate P, V, etc.

---
# In-Class notes and Problems
- The sum of r *independent* Geometric(p) is Negative Binomial(r, p)
- The sum of n *independent* Bernoulli (p) is Binomial (n, p)
- The sum of m *independent* Binomial (n, p) is Binomial (mn, p)
- The sum of m *independent* Negative Binomial (r, p) is Negative Binalmial (mr, p)

## Geometric Distribution
![[Pasted image 20240409234425.png]]
>[!abstract] Properties of Geometric: 
>> 1. **UnFixed X possible values** : x= 1, 2, ...
>> 2. **Only 2 possibilities**: Succeed(p)/Failure (1-p)
>> 3. PMF = $p(1-p)^{x-1}$
>> 4. $E(X)=\frac{1}{p}$
>> 5. $V(X)=\frac{1-p}{p^2}$
## Negative Binomial
![[Pasted image 20240409235028.png]]
>[!abstract] Properties of Negative Binomial: 
>> 1. **UnFixed X possible values** : x= r, r+1, ...
>> 2. **Only 2 Possible outcomes**: Succeed (p)/Failure (1-p)
>> 3. **Number of successes: ** *r*
>> 4. PMF = $\binom{x-1}{r-1}*p^r(1-p)^{x-r}$
>> 5. $E(X)=\frac{r}{p}$
>> 6. $V(X)=\frac{r(1-p)}{p^2}$
>>>[!tip] Negative Binomial can be seen as n independent Bernoulli trials until get r successes 

>[!note] Relationship between Geometric and Negative Binomial
>![[Pasted image 20240409235710.png]]

---
# Review List & Flashcards
1. Geometric：Definition，Properties，PMF，E (X), V (X)
2. Negative Binomial: Definition, Properties, PMF, E (X), V (X)
3. Relationship between Binomial, Bernoulli, Geometric, Negative Binomial
	- The sum of r *independent* Geometric (p) is Negative Binomial (r, p)
	- The sum of n *independent* Bernoulli (p) is Binomial (n, p)
	- The sum of m *independent* Binomial (n, p) is Binomial (mn, p)
	- The sum of m *independent* Negative Binomial (r, p) is Negative Binalmial (mr, p)