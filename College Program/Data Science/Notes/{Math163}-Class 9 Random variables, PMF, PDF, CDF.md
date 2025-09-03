---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - flashcards/Math
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math163_Lecture04.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Discrete/Continuous RV
>	1. Know difference between discrete and continuous
>2. PMF, PDF, CDF
>	1. Know definition and notation of PMF($f(x)$), PDF($f(x)$), CDF ($F(X)$)
>	2. Know the meaning of PDF, PMF, CDF
>		1. 
>	3. Their properties

>[!abstract] Problem solving
>1. How to calculate Probability through PMF($p(x)$)/PDF ($f(x)$)
>	1. $p(a)=P(X=a)$
>	2. $P(X \in B)=\int f(x)dx$
>2. How to get CDF through PMF/PDF
>	1. $\sum\limits_{}^{}p(a)$
>	2. $\int\limits_{-oo}^{a}f(x)dx$


---
# In-Class Problems
## Random Variable
![[Math163_Lecture04.pdf#page=1&rect=68,463,516,564|Math163_Lecture04, p.1]]
## PMF，PDF，CDF

The probability mass function (**PMF**) of a discrete random variable is defined as the function---> $p(a)=P(X=a)$
<!--SR:!2024-10-05,3,250-->

The probability density function (**PDF**) of a continuous random variable X is: ---> $P(X \in B)=\int_{B} f(x)dx$
<!--SR:!2024-10-05,3,250-->

The cumulative distribution function (**CDF**) of the random variable X is ---> $F(a)=P(X\leq a)$
<!--SR:!2024-10-05,3,250-->
### The meaning of PDF,PMF
>[!note] the area in range B of PDF is the probability P (B)
![[Math163_Lecture04.pdf#page=3&rect=152,511,416,604|Math163_Lecture04, p.3]]
### Important properties for them
- The sum of all value of the PMF is 1
- If integrated over all possible values of X (or the whole of R) for PDF we must obtain one
- For continuous variable , the probability at x= a single value is 0
- The CDF is always non-decreasing, right-continuous
> [!PDF|red] [[Math163_Lecture04.pdf#page=4&selection=6,0,11,2&color=red|Math163_Lecture04, p.4]]
> >[!faq] The cumulative distribution function of a random variable X is given by

### The relation between PDF f (x) and CDF F (a)
- $F(a) = \int \limits_{-\infty}^{a} f(x)dx$
---

# Flash Cards
