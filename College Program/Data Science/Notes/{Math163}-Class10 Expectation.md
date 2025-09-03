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
>1. Know the definition of  [[#Expected Value]] for discrete and continuous RVs
>2. Know how to get $E[g(x)]$
>	1. [[#^discretecase]]
>	2. [[#^continuouscase]]
>3. Know why $E[X]=\int \limits_{0}^{\infty}P(X>y)dy$ [[#^lemma]]
>4. Know the [[#Linear combination]] of E
>5. Know how to calculate E for a RV given the f (x)

---
# In-Class Problems
> [!PDF|red] Example 39 [[Math163_Lecture04.pdf#page=4&selection=108,2,113,45&color=red|Math163_Lecture04, p.4]]
> >[!faq] An insurance company determines that N , the number of claims received in a week, is a random variable with

## Expected Value
![[Math163_Lecture04.pdf#page=5&rect=67,549,501,631&color=red|Math163_Lecture04, p.5]]
![[Math163_Lecture04.pdf#page=5&rect=69,348,499,444&color=red|Math163_Lecture04, p.5]]
### Linear combination
E[aX+b] = ---> aE[X]+b
> [!PDF|red] Example 42 [[Math163_Lecture04.pdf#page=6&selection=58,0,80,12&color=red|Math163_Lecture04, p.6]]
> >[!faq] Find E[aX + b] in terms of E[X] if a, b ∈ R are constant


> [!PDF|red] Theorem [[Math163_Lecture04.pdf#page=6&selection=55,0,55,6&color=red|Math163_Lecture04, p.6]]
> ![[Math163_Lecture04.pdf#page=6&rect=69,617,501,683&color=red|Math163_Lecture04, p.6]]
> >[!faq] Proof:

^discretecase

> [!PDF|red] Example 43 [[Math163_Lecture04.pdf#page=6&selection=84,0,89,82&color=red|Math163_Lecture04, p.6]]
> >[!faq] A tour operator has a bus that can accommodate 20 tourists. The operator knows that tourists may not show up, so he sells 21 tickets. The probability that an individual tourist will not show up is 0.02, independent of all other tourists. Each ticket costs 50, and is non-refundable if a tourist fails to show up. If a tourist shows up and a seat is not available, the tour operator has to pay 100 (ticket cost + 50 penalty) to the tourist. Calculate the expected revenue of the tour operator.

![[Math163_Lecture04.pdf#page=7&rect=68,592,464,670|Math163_Lecture04, p.7]]^lemma
>[! faq] Proof:
$$
\begin{flalign} 
P(Y>y) = 1- CDF&&\\
\int_{0}^{\infty}  \int_{y}^{\infty} f(x)   dx \, dy  =\int_{0}^{\infty}  \int_{0}^{x} f(x)   dy  \,dx&&\\
 
\end{flalign}
$$

Here $f(x)$ is a constant respect to y
![[Math163_Lecture04.pdf#page=7&rect=69,386,500,461|Math163_Lecture04, p.7]] ^continuouscase
>[! faq] Proof:

$$
\begin{align}
E[g(x)]=\int_{0}^{\infty} \int_{x in g(x)>y}^{\infty} f(x) \, dx  \, dy\\ \\
= \int_{x in g(x)>0}^{\infty} \int_{0}^{g(x)} f(x) \, dy  \, dx\\ \\
=\int_{x in g(x)>0}^{\infty} f(x)\int_{0}^{g(x)} 1 \, dy  \, dx\\ \\
=\int_{-\infty}^{\infty} g(x)f(x) \, dx 
\end{align}
$$ 
> [!PDF|red] example 44 [[Math163_Lecture04.pdf#page=7&selection=80,0,80,65&color=red|Math163_Lecture04, p.7]]
> >[!faq] A stick of length 1 is split at a point U having density function, Determine the expected length of the piece that contains the point p (0 ≤ p ≤ 1).
> >Let Lp represent the length of the substick that contains p
> 


---

# Flash Cards
