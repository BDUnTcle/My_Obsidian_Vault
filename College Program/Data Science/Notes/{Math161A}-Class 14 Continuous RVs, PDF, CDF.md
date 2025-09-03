---
create date: 2024-03-12
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#flashcards"
  - review
  - Math
  - Math/Probability
modification date: 2024-03-12T11:21:00
type: CourseNotes
sr-due: 2024-03-22
sr-interval: 5
sr-ease: 230
---
[[#Review List]]
# Before the Class
Read: 4.1, 4.2
1. Piece defined function
2. Lableled graph
3. Integral/integrate 
4. derivative/anti-derivative
## Lectures and Materials
[[Math161A_Lecture07.pdf]]

[[《Probability and Statistics for Engineering》.pdf]]
- Ch 4.1 (p.138)
- Ch 4.2

---
# In-Class Problems
## Continuous RV(Random Variables)
![[Pasted image 20240317171216.png]]
## PDF (Probability Density Function)
![[Pasted image 20240312134313.png]]
### Representation :
![[Pasted image 20240312140605.png]]
### Proposition
- There is always $P(X=c)=0$
- The density $f(x)$ is defined on the entire real line, but may be zero on an interval
- $f(x)>=0$ for all R
- $P(a<=X<=B)=P(a<=X<b)=P(a<X<=b)=P(a<X<b)$
- $\int f(x)dx=1$
---
## CDF (Cumulative Distribution Function)
![[Pasted image 20240312141217.png]]
### Proposition
- You can obtain the PDF $f(x)$ from the CDF $F(X)$
	- $f(X)=F'(X)$
- The CDF can be used to compute probabilities for a continuous random variable:
	- $P(X<a)=F(a)$
	- $P(X>a)=1-F(a)$
	- $P(a<X<b)=F(b)-F(a)$
---
## Examples
---
# Review List
>[! abstract] Main Topics
>1. Definitions of continuous RV, PDF, CDF
>2. How to **represent** RV, PDF, CDF
>3. The differences between continuous and discrete situation
>4. 5 [[#Proposition]] of PDF
>5. 2 proposition of CDF
>6. How to use PDF and CDF to calculate probabilities
>7. How to calculate CDF and PDF
---
# Flash Cards

**Definition and Representation of PDF P(X)**
???
Probability Density Function of $X$ is a function $f(x)$ such that for any 2 numbers a and b: $P(a\leq X\leq b)=\int_a^bf(x)dx$,
which means the **area** between a ~ b in $f(x)$
<!--SR:!2024-04-27,30,270-->

**Definition and Representation of continuous CDF F(x)**
???
$F(x)=P(X\leq x)=\int_{-\infty}^xf(y)dy$,
which means the **area** under the curve $f(x)$ to the **left** of x.
<!--SR:!2024-05-22,36,241-->