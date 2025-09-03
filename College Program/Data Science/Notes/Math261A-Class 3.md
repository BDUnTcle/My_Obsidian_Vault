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
- [[Math261A_Lecture02.pdf]]
- [[Math261A-Class 2]]
---
# Review List
>[! abstract] Main Topics
>1. Properties of least-squares estimators
>2. The meaning of Inference for the linear regression model (things about population parameter with calculated parameter)
>	1. What is $SS_{T}$, $SS_{Res}$ and $SS_{R}$
>	2. What is $MS_{Res}$

---
# In-Class Problems
## Properties of Least-Squares Estimators
>[!info] Both parameter estimates can be written as linear combinations of the observations $y_i$
>> $\hat{\beta_1}=\frac{S_{xy}}{S_{xx}}=\sum\limits_{i=1}^{n}c_{i}y_i$, where $c_i=\frac{(x_i-\overline{x})}{S_{xx}}$
>> ![[Pasted image 20240905073723.png]]
### The Proof that $\hat{\beta_{1}}$ is unbiased
> [!PDF|red] [[Math261A_Lecture02.pdf#page=5&selection=104,0,109,12&color=red|Math261A_Lecture02, p.5]]
> >[!faq] Show that $E(\hat{\beta_1})=\beta_1$ is unbiased.
> >> A: $E(\hat{\beta_1})=\beta_1$

### The proof that the variance of the estimated regression parameters $\hat{\beta_{0}}$, $\hat{\beta_{1}}$

---
## Gauss-Markov Theorem
#flashcards/Math
In a simple linear regression model in which the **residuals** are {{uncorrelated}} , with mean {{zero}} and {{equal}} variances.
<!--SR:!2024-10-05,3,250!2024-10-05,3,250!2024-10-05,3,250-->

> [!PDF|] Degree of Freedom [[Math261A_Lecture02.pdf#page=6&selection=107,22,109,31|Math261A_Lecture02, p.6]]
> > A degree of freedom of a parameter estimate is the number of observations that go into an estimate that could be varied (without changing the estimate)
## $MS_{Res}$ $SS_{T}$, $SS_{Res}$ and $SS_{R}$
In a simple linear regression model $MS_{Res}$ means: ---> **the unbiased estimated residual variance/mean-square residual** $= \hat{\sigma} ^2=\frac{SS_{res}}{n-2}$
<!--SR:!2024-10-05,3,250-->

> [!PDF|note] $MS_{Res}$ [[Math261A_Lecture02.pdf#page=6&selection=127,0,127,48&color=note|Math261A_Lecture02, p.6]] 
> >[!faq] An unbiased estimate for the residual variance is
> >>[!tip] $MS_{Res}=\hat{\sigma}=\frac{SS_{Res}}{n-2}$

In a simple linear regression model $SS_{T}$ means: ---> **the total sum of squares** $= \sum\limits_{i=1}^{n}(y_{i}-\bar{y})^2=\sum\limits_{i=1}^{n}y_{i}^2 -n\bar{y}^2$
<!--SR:!2024-10-05,3,250-->


> [!PDF|note] $SS_{T}$ [[Math261A_Lecture02.pdf#page=6&selection=177,0,180,52&color=note|Math261A_Lecture02, p.6]]
> >[!faq] $SS_{T}$ is the total sum of squares which can be computed as 
> >$SS_{T}=\sum\limits_{i=1}^{n}(y_{i}-\bar{y})^2=\sum\limits_{i=1}^{n} y^2-n\bar{y}^2$

> [!PDF|note] $SS_{R}$ [[Math261A_Lecture02.pdf#page=9&selection=80,0,86,7&color=note|Math261A_Lecture02, p.9]]
> >[!faq] $SS_{R}$ is called the regression sum of squares, where
> > $SS_{R}=\sum\limits_{i=1}^{n}(\hat{y}-\bar{y})^2=\hat{\beta_{1}}S_{xy}$
> 
> 

> [!PDF|red] [[Math261A_Lecture02.pdf#page=6&selection=226,0,227,24&color=red|Math261A_Lecture02, p.6]]
> >[!faq] Find the residual variance estimate for the Rocket Propellant data example from the R output.


---
# Flash Cards
