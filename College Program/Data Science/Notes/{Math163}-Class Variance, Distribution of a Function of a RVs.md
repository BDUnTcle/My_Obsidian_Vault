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
---
# Review List
>[! abstract] Main Topics
>1. Know the [[#Definition]] of Variance
>	1. Be able to prove [[#^proof1]]
>2. Be able to calculate V given PMF f (x)
>	1. [[#^69f2ec]]
>3. Know the [[#Linear combination]] of V
>4. Be able to get the [[#Distribution of a Function of a RV]]
>	1. [[#^db8681|Example 48]], [[#^28b73f|Example 49]]
>	2. [[^theorem]]

>[!abstract] Problem Solving
>1. Given the distribution of X, find the distribution (CDF, PMF, PDF) of Y =g(X)
>2. Compute probabilities for Y = g(X), given the distribution of X

---
# In-Class Problems
## Definition
![[Math163_Lecture04.pdf#page=8&rect=57,613,501,682&color=red|Math163_Lecture04, p.8]]
![[Math163_Lecture04.pdf#page=8&rect=61,512,496,611&color=red|Math163_Lecture04, p.8]] ^proof1

> [!PDF|red] Example 45 [[Math163_Lecture04.pdf#page=8&selection=83,0,88,8&color=red|Math163_Lecture04, p.8]]
> >[!faq] Let X be a continuous Uniform (a, b) random variable with density function
> 

^69f2ec
## Linear combination
$V[aX+b]$ = ---> $a^2V[X]$
> [!PDF|red] Example 46 [[Math163_Lecture04.pdf#page=9&selection=6,0,31,13&color=red|Math163_Lecture04, p.9]]
> >[!faq] Let X be a random variable (discrete or continuous) with variance σ2. Find V ar (aX + b), where a, b ∈ R are constants

## Distribution of a Function of a RV
>[!question]
> ![[Math163_Lecture04.pdf#page=10&rect=70,663,498,697&color=red|Math163_Lecture04, p.10]]

> [!PDF|red] Example 48 [[Math163_Lecture04.pdf#page=10&selection=26,0,46,0&color=red|Math163_Lecture04, p.10]]
> >[!faq] Let X be a continuous random variable with CDF FX (x). Find the CDF of Y = X 2

^db8681

> [!PDF|red] Theorem [[Math163_Lecture04.pdf#page=10&selection=50,0,88,45&color=red|Math163_Lecture04, p.10]] ^theorem
> >[!faq] Let X be a continuous random variable with probability density function fX (x). Suppose that g (x) is a strictly monotonic (increasing or decreasing), differentiable (and thus continuous) function of x. Then the random variable Y defined by Y = g (X) has a probability density function given by
> > ![[Math163_Lecture04.pdf#page=10&rect=131,448,434,498&color=red|Math163_Lecture04, p.10]]

> [!PDF|red] Example 49 [[Math163_Lecture04.pdf#page=10&selection=155,0,180,0&color=red|Math163_Lecture04, p.10]]
> >[!faq] Let X be a continuous nonnegative random variable with density function f and let Y = Xn. Find fY , the density function of Y

^28b73f

---

# Flash Cards
