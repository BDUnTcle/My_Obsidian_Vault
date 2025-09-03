---
create date: 2024-09-10
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
- [[Math261A_Lecture03.pdf]]
- [[线性代数学习目录]]
---
# Review List
>[! abstract] Main Topics
>1. Definition of multiple linear regression
>2. Estimation of the Model Parameters
>3. Properties of the Least Squares Estimators

---
# In-Class Problems
## Definition
> [!PDF|yellow] [[Math261A_Lecture03.pdf#page=1&selection=62,0,113,2&color=yellow|Math261A_Lecture03, p.1]]
> >[!faq] A multiple linear regression model with k predictor variables $X_{1}, X_{2}, ..., X_{k}$ and a response $Y$ , can be written as: $y =\beta_{0} +\beta_{1} x_{1}+\beta_{2} x_{2} +\dots \beta_{k} x_{k}+\epsilon$.
> 
> 
---

## Estimation of the Model Parameters
![[Math261A_Lecture03.pdf#page=4&rect=64,337,508,445&color=yellow|Math261A_Lecture03, p.4]]

![[Math261A_Lecture03.pdf#page=5&rect=65,448,513,721&color=yellow|Math261A_Lecture03, p.5]]
> [!PDF|red] [[Math261A_Lecture03.pdf#page=6&selection=66,0,77,1&color=red|Math261A_Lecture03, p.6]]
> >[!tip] $\hat{\beta}$, $\hat{y}$ and $\epsilon$
> > 1.  $\hat{\beta} = (X^{\prime} X)^{-1} X^{\prime} y$
> > 2. $\hat{y}=X \hat{\beta}=X(X^{\prime}X)^{-1}X^{\prime}y=Hy$
> > 3. $\epsilon=y-\hat{y}=y-X\hat{\beta}=(I-H)y$

### The Delivery Times Data
[[Math261A_Lecture03.pdf#page=7&selection=6,0,6,23&color=important|Math261A_Lecture03, p.7]]
![[Excalidraw/R output for SLR model.excalidraw.md#^area=p8ICzsVaapvcqVJZbR2jS|ROutputMLR]]
- Estimated value for $\hat{\beta}$: in the blue circle ($\hat{\beta_{0}}=2.341$, $\hat{\beta_{1}}=1.6159$...)
- Standard Error for each $\hat{\beta}$ for hyphothesis test/CI for individual coefficient (orange)
- T value and p value for significance (purple
- ANOVA Table
	- $SS_{R}$ = sum of SS for each predictors
	- $SS_{RES}=233.7$, $MS_{RES}=\hat{\sigma}^2=\frac{SS_{RES}}{df=22}=10.6$
## Properties of the Least Squares Estimators
> [!PDF|red] [[Math261A_Lecture03.pdf#page=10&selection=7,1,13,17&color=red|Math261A_Lecture03, p.10]]
> >[!faq] The least squares estimate vector ˆβ in the multiple linear regression model is unbiased


> [!PDF|red] [[Math261A_Lecture03.pdf#page=10&selection=17,0,20,1&color=red|Math261A_Lecture03, p.10]]
> >[!faq] Find the covariance matrix of the least squares estimate vector ˆβ.
> 
> 
---
# Flash Cards
