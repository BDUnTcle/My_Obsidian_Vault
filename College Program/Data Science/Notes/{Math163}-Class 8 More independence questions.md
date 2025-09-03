---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#flashcards"
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math163_Lecture03.pdf]]
---
# Review List
>[! abstract] Main Topics
>- The proposition of independence
>- More independent probability questions:
>> 1. [[#The coupon collector problem]]
>> 2. [[#The problem of points]]
>> 3. [[#The gambler's ruin problem]]

---
# In-Class Problems        
## Proposition proof
![[Math163_Lecture03.pdf#page=7&rect=66,228,456,275|Math163_Lecture03, p.7]]
>[!hint] Proof:
> 1. ~ $P(E\cap F)=P(E)P(F)$,
> 2.  $P(E\cap F^c)=P(E)-P(E\cap F)=P(E)-P(E)P(F)=P(E)(1-P(F)=P(E)P(F^c)$ 
> 	- ! (Using the partition trick: $P(E)=P(E\cap F)+P(E\cap F^c)$)

## The coupon collector problem

![[Math163_Lecture03.pdf#page=8&rect=70,641,501,719|Math163_Lecture03, p.8]]
- $ Event $A_{i}$ represents at least 1 type of i coupons among those selected $$
\begin{equation}
\begin{split}
P(A_{i})
&=1-P(\text{none of those collected coupons are type i})\\
&=1-(1-P_{i})^k
\end{split}
\end{equation}
$$
- $ $A_{i}\cup A_{j}$ = at least one of those coupons are i or j $$\begin{equation}
\begin{split}
P(A_{i}\cup A_{j}) 
&= 1- P(\text{Neither of those coupons are i or j})\\
&= 1-(1-(p_{i}+p_{j}))^k
\end{split}
\end{equation}
$$
- $ $$\begin{equation}
\begin{split}
P(A_{i}|A_{j})
&=\frac{P(A_{i}\cap A_{j})}{P(A_{j})}\\
&=\frac{P(A_{i})+P(A_{j})-P(A_{i}\cap A_{j})}{P(A_{j})}\\
&=\frac{1-(1-P_{i})^k+1-(1-P_{j})^k-1-(1-(p_{i}+p_{j}))^k}{1-(1-P_{j})^k}

\end{split}
\end{equation}

$$


## The problem of points
![[Math163_Lecture03.pdf#page=9&rect=70,607,502,721&color=yellow|Math163_Lecture03, p.9]]
we can define the event <mark style="background: #FF5582A6;">E : exactly k successes in n+m-1 trials</mark>
Then we could know that $E\sim Binomial(n=n+m-1,r=k)$
Then:
	$P(E)=\binom{n+m-1}{k}p^k(1-p)^{n+m-1-k}$
We want to find the P of <mark style="background: #FFB86CA6;">n successes occur before m failures</mark>，which means **k is no less than n** 
$P=\sum \limits_{k=n}^{n+m-1}\binom{n+m-1}{k}p^k(1-p)^{n+m-1-k}$
## The gambler's ruin problem

# Flash Cards
