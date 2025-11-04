---
create date: 2024-09-11
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
- [[Math163_Lecture04.pdf]]
- [[ContinuousDistributions.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Know 3 named continuous distributions
>	1. [[#Uniform (a, b)]]
>	2. [[#Exponential~(λ)]] and "memotyless property"
>	3. [[#Gamma (r,λ)]]
>		1. Know [[#The Gamma Function $ Gamma(r)$]]
>		2. Be able to use the [[#"Gamma Trick"]]
>2. Know [[#Normal (μ, $ sigma 2$)]]
>	1. Know [[#Important facts of Normal]]
>	2. Know [[#The DeMoivre-Laplace Limit Theorem]] and its meaning in graph
>	3. Know [[#Normal approximation to the Binomial]]
>3. Know [[#Chi-Squared Distribution]]
>	1. Know the relationship betwwen Chi-Square and Gamma
>	2. Know the parameter n(degree of freedom) of Chi-Square
>	3. Know what the curve looks like
>	4. Know E (x) and V (x) of it
>	5. Know [[#The relationship between Normal and Chi-Square]]
>	6. Know [[#Important Facts of Chi-Square]]

---
# In-Class Problems
## Uniform (a, b)
![[Math163_Lecture04.pdf#page=15&rect=70,514,500,695&color=red|Math163_Lecture04, p.15]]
## Exponential~(λ)
>[!tip] The exponential distribution is the continuous analog to the geometric distribution
![[Math163_Lecture04.pdf#page=15&rect=67,281,501,458&color=red|Math163_Lecture04, p.15]]
## Gamma (r,λ)
![[Math163_Lecture04.pdf#page=16&rect=69,637,500,721&color=red|Math163_Lecture04, p.16]]
### The Gamma Function $\Gamma(r)$
- If r is a **integer**, then $\Gamma(r)=(r-1)!$
- For general r, $\Gamma(r) = \int \limits_{0}^{\infty}e^{-y}y^{r-1}\,dy$
### "Gamma Trick"
## Normal (μ, $\sigma^2$)
![[Math163_Lecture04.pdf#page=16&rect=59,216,496,293&color=red|Math163_Lecture04, p.16]]
### Important facts of Normal
 - **Standard Normal**
	 - With mean 0 and variance 1
	 - CDF denoted by $\phi(x)=P(X\leq x)$
 - The sum of independent normal is normal ![[Math163_Lecture04.pdf#page=17&rect=70,568,501,629&color=red|Math163_Lecture04, p.17]]
### The DeMoivre-Laplace Limit Theorem
>[!note]  How to get $P(a\leq X\leq b)$ for n independent normal distribution
![[Math163_Lecture04.pdf#page=17&rect=70,364,499,450&color=red|Math163_Lecture04, p.17]]

### Normal approximation to the Binomial
> [!PDF|red] Example 57 [[Math163_Lecture04.pdf#page=17&selection=197,0,230,70&color=red|Math163_Lecture04, p.17]]
> >[!faq] Consider X ∼ Binomial (n = 10, p = 0.3). Use your calculator to compute P (3 ≤ X ≤ 6). Also use the normal approximation to the Binomial (with continuity correction) to approximate this same probability. Use either your calculator or a normal table to look up the required normal CDF values

## Chi-Squared Distribution
![[Math163_Lecture04.pdf#page=18&rect=64,566,438,643&color=red|Math163_Lecture04, p.18]]
- @ The chi-square is a special case of the gamma with λ=1/2 , and r = n/2
![[Math163_Lecture04.pdf#page=18&rect=161,319,409,506&color=red|Math163_Lecture04, p.18]]
### Mean and Variance of Chi-Square
- $E[X]=n$
- $V (X) = 2 n$
### The relationship between Normal and Chi-Square
- @ the square of standard normal Z has a Chi-Square distribution
> [!PDF|red] Exapme 58 [[Math163_Lecture04.pdf#page=18&selection=169,0,186,12&color=red|Math163_Lecture04, p.18]]
> >[!faq] Let Z ∼ Normal (0,1). Show that Z 2 has a χ2 1 distribution

### Important Facts of Chi-Square
![[Math163_Lecture04.pdf#page=19&rect=70,656,501,719&color=red|Math163_Lecture04, p.19]]

---

# Flash Cards
